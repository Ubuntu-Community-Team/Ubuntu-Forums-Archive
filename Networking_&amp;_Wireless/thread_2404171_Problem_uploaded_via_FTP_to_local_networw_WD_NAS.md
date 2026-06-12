---
title: "Problem uploaded via FTP to local networw WD NAS"
date: 2018-10-20
forum: Networking &amp; Wireless
---

### Post by GrouchyGaijin on 2018-10-20
Both the NAS and my local machine or om my local network.

When I mirror my Dropbox folder to the NAS I am able to keep a prefectly uptodate Dropbox folder in my NAS.

The script to do this is run by a cron job.

```
#!/bin/bash#By GrouchyGaijin
#Last Updated: Sun 15 Apr 2018 07:56:28 PM MDT
echo "This script is for LFTP Backup to NAS/John from Dropbox"
set ssl:verify-certificate no [COLOR=#0000ff](No is because everything is totally behind my local network firewall)[/COLOR]
HOST='192.168.1.xxx' ([COLOR=#0000cd]The last part of the inteternations ip-address)[/COLOR]
USER='xxxxxx
PASS=''xxxxx
TARGETFOLDER='/john/Dropbox'
SOURCEFOLDER='/home/john/Dropbox'


lftp -f "
open $HOST
user $USER $PASS
lcd $SOURCEFOLDER
mirror --reverse --delete --verbose $SOURCEFOLDER $TARGETFOLDER
bye
"
gxmessage -name "Dropbox Backup" -timeout "15" -buttons "Close:1" -default "Close" -center -font "serif 12" -fg "#919191" -bg "#041729" -wrap -title "Dropbox Backup" -file /home/john/scripts/dropbox-backup-finished.txt


echo "This script is for LFTP Backup to NAS/John from scripts"
set ssl:verify-certificate no
HOST='192.168.1.xxx'
USER=''xxxxx"
PASS=''xxxxx"
TARGETFOLDER='/john/scripts'
SOURCEFOLDER='/home/john/scripts'


lftp -f "
open $HOST
user $USER $PASS
lcd $SOURCEFOLDER
mirror --reverse --delete --verbose $SOURCEFOLDER $TARGETFOLDER
bye
"
gxmessage -name "Scripts Backup" -timeout "15" -buttons "Close:1" -default "Close" -center -font "serif 12" -fg "#919191" -bg "#041729" -wrap -title "Scripts Backup" -file /home/john/scripts/scripts-backup-text.txt



```

This script, when the last part of the IP address dress is not covered up works perfectly every time.

When I tried changing the command form "mirror" to something like "put - the script fails every time. There are some spaces in the file names and directory names. I tried to heal by adding " quotation marks", around those paths.

[COLOR=#ff3333]Does anyone know the cause of the problems I having when I attempt to upload (NOTE this is not a mirror) *.mp3 from a specific direction to an directory on the NAS?? Thank you![/COLOR]

---

