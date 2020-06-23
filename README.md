## What is this?

Simply put, this is a shell script (`imx.sh`) that extracts the text of all messages from an iMessage database, and places them in a series of text files organized by telephone number. It works on recent versions of macOS - it has been verified to work on Catalina 10.15.5. There has been no extensive testing to date; this should be considered experimental software. 

## Working with Apple's security
The simplest method to enable `imx.sh` to run is to give the `Terminal.app` Full Disk Access in `System Preferences`.

## What is the provenance of this code? 

Please refer to the Wiki. 

## How do I use this? 

1. Copy the script to your local machine - at least two ways to do this: 

    - My *preferred* way is that you fork or clone this repo, and submit pull requests to incorporate any improvements you think worthwhile. 

    - Another way is to simply copy the contents of `imx.sh` to your machine, save it as a file and make it executable using `chmod 755 ./imx.sh`
    
2. Once you have an executable copy of `imx.sh`, `cd` to that folder - e.g. `cd /Users/<yourusername>/MyScripts`: 

    ```
    mkdir extract
    ./baskup.sh
    ```

    Depending upon the size of your iMessage database & the other usual variables, this should finish "quickly" - 2-10 seconds? When it completes, you will find the folder you created is now populated with a series of folders and files. You may review them using `less`, which should result in something similar to the following. Note that this output reflects only two "conversations" in the database - you may have more than that. In this context a "conversation" is simply another number/person with whom you have exchanged messages: 
    
    ```
    ls -lR ./extract | less 
     % ls -lR ./backup
    total 0
    drwxr-xr-x  4 tuser  staff  128 Jun 21 21:55 +12345678901
    drwxr-xr-x  4 tuser  staff  128 Jun 21 21:55 +12345074321

    ./backup/+12345678901:
    total 32
    drwxr-xr-x  2 tuser  staff     64 Jun 21 21:55 Attachments
    -rw-r--r--@ 1 tuser  staff  16361 Jun 22 01:10 iMessage;-;+12345678901.txt

    ./backup/+12345678901/Attachments:

    ./backup/+12345074321:
    total 8
    drwxr-xr-x  2 tuser  staff  64 Jun 21 21:55 Attachments
    -rw-r--r--  1 tuser  staff  83 Jun 22 01:10 iMessage;-;+12345074321.txt

    ./backup/+12345074321/Attachments:
    ```

    Also note that `ls -lR` is the **recursive** form of the *list* command, and so we see everything in the `./extract` folder listed. The text files (e.g. `iMessage;-;+12345678901.txt` may be opened in your text editor, and/or processed by another script. Each message is a 'record' in the file formatted roughly as follows: 
    
    >Name (Me or Friend) | Text of message | date-time stamp
    
    There is a single option available with imx.sh: `imx.sh -a`. This option will extract all media (pictures, sound, video) and files found in the iMessage database. They are organized by "conversation" in the subfolder named `Attachments`.

<!---  BEGIN HIDDEN TEXT
To use baskup:

Download Baskup from this page by clicking download zip in the top right corner and then unzip the download

From terminal:

![alt tag](https://cloud.githubusercontent.com/assets/5935411/8760632/23ce21b8-2cee-11e5-80d7-37c97505cd17.JPEG)

1. Run: cd (path of the downloaded baskup folder, i.e *cd ~/Downloads/baskup-master*)

2a. Run: *bash baskup.sh* to only backup messages 💬

2b. Run: *bash baskup.sh -a* to backup messages AND attachments 💬 + 📎

Your bask-up master folder will now begin to be filled with your backups. This may take some time, so be patient.

## All done
![alt tag](https://cloud.githubusercontent.com/assets/5935411/8760633/272d34c0-2cee-11e5-87c7-084d3bc8f21f.png)


#### Each folder will be named after the contact's phone number. Group chat's will be identified as "chat XYZ"

![alt tag](https://cloud.githubusercontent.com/assets/5935411/8760635/29201a04-2cee-11e5-9cc7-668b6a6e5ee0.png)

#### Within each directory you will find a directory for the attachments from that message, and the actual message text file. 

## Opening an issue

When opening an issue, please note the issue as either related to the bash script or the macOS version of baskup. For macOS, please include the version number in your issue log.

--->
