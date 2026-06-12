---
title: "Bash Scripting Help Please"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by sharkllama on 2009-07-28
Hi, 
   Complete noob to bash scripting.  I've written a very simple backup script which calls rsync and is eventually intended to be used with anacron (sp?).  This is done by mounting all the drives, then checking to see that the drives are mounted, then calling rsync to copy data if needed.  I get the following output at the shell when I call the script, which I don't understand:

sharkllama@quaaludes:~/Scripts/Bash$ sh ./simpleBackupScript.sh 

[: 13: missing ]
[: 20: missing ]
[: 27: missing ]

As far as I can tell (which isn't very far) my syntax is correct and I should be performing all the rather simple operations correctly.  I've attached the script.  Thanks for you help.
-Brant

#!/bin/bash
#
# A simple backup script using rsync that mirrors data from a series of 
# partitions from one hardware to another.  There are three different partition
# to be mirrored: Linux Filesystem, Windows and a shared Data partition
#

# Paths of Backup Partitions
LINUX_BACKUP_DIR="/mnt/backupDisk/Linux/"
WINDOZE_BACKUP_DIR="/mnt/backupDisk/Windows/"
DATA_BACKUP_DIR="/mnt/backupDisk/Data/"

# Mount all the hard-drives
echo `sudo mount -a`

# Check to see if the backup partition is mounted.  If so then call rsync to
# back up the partition
DF_OUTPUT=`df $LINUX_BACKUP_DIR`
if [ -n "$DF_OUTPUT"]
	then
		echo "$LINUX_BACKUP not empty!"
		echo `rsync -avhxv / $LINUX_BACKUP_DIR`
fi

DF_OUTPUT=`df $WINDOZE_BACKUP_DIR`
if [ -n "$DF_OUTPUT"]
	then
		echo `rsync -avhxv /windows/ $WINDOZE_BACKUP_DIR`
		echo "$WINDOZE_BACKUP_DIR not empty!"
fi

DF_OUTPUT=`df $DATA_BACKUP_DIR`
if [ -n "$DF_OUTPUT"]
	then
		echo "$DATA_BACKUP_DIR not empty!"
		echo `rsync -avhxv /mnt/media/ $WINDOZE_BACKUP_DIR`
fi

---

### Post by lavinog on 2009-07-29
I think you need to remove the sudo line and chown the script to root so only super user can modify it and run it.
```
echo `sudo mount -a`
```
won't do any good if you cron this as a regular user, since you have to enter a password.

also:
For shell expansion: use of $(command) is preferred to `command` because of better nesting.

You might want to mount your backup drive to /media/backupDisk/... instead of /mnt. I don't have a reason why except I remember reading that debian prefers to use media for mountpoints

---

### Post by shel-hall on 2009-07-29
I think you need spaces both before and after the square brackets in the statements on lines 13, 20, and 27.

The left bracket is actually a command, so, like any command, it has to be delimited with spaces.

-Shel

---

### Post by sharkllama on 2009-07-29
Excellent.  Thanks guys, the spaces (or lack thereof) were the issue.  Changing permissions would have been an issue in the near future so thanks for the pre-emptive troubleshooting there.
-Brant

---

### Post by starcannon on 2009-07-29
Here are some very good e-books, one even includes a VERY basic backup script. I use these materials regularly for my own bashing around in the terminal.

GL and HF

[Very Simple Backup Script]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO-2.html")

[Introduction]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")

[Advanced]("http://tldp.org/LDP/abs/html/")

---

