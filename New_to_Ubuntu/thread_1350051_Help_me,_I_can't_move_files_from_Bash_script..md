---
title: "Help me, I can't move files from Bash script."
date: 2009-12-08
forum: New to Ubuntu
---

### Post by outleradam on 2009-12-08
Hello, I'm new to Ubuntu and Bash programming.   I have created a #!bin/bash script which will rename and move myth recordings, then make a symlink back to the original file. 

It works GREAT from the Shell terminal, however, when MythTV tries to run the program, it experiences 2 issues.

1. File will not move
2. notify-send will not send notifications.

How can I correct this what does my terminal have that Myth does not have?


The following is a log from the program I created.  I hope it can help. I'm really lost!
```
@@@@@@@@@@NEW SEARCH INITIATED AT Tue Dec  8 21:34:41 CST 2009@@@@@@@@@@@@@
SEARCHING: www.TheTvDb.com SHOW NAME: South Park EPISODE: Freak Strike
FILE NAME: /var/lib/mythtv/recordings/1037_20091203193000.mpg
SEARCH FOUND:South Park ID#: 75897
DEFINED ABSOLOUTE EPISODE NUMBER: 104
#########################################################
###################DEBUG MODE ENABLED####################
#########################################################
LISTING INTERNAL VARIABLES USED BY BashSExx. VERIFY THESE ARE NOT EFFECTED BY GLOBAL VARIABLES
INTERNET TIMEOUT:50- TvDb API KEY:6DF511BB2A64E0E9- BashSExx WORKING DIR:/home/mythtv/BashSExx-
MOVE DIR:/mnt/NAS/Video/shows- USING SHOWNAME AS FOLDER:UseShowNameAsDir-
Disable File Move:Disabled Notifications:Enabled Debug Mode:Enabled
INPUT SHOW NAME:South Park- LOCAL SHOW NAME TRANSLATION:- SENT TVDB SHOW NAME:South%20Park-
RESOLVED SERIES ID:75897- RESOVED SHOW NAME:South Park- I
NPUT EPISODE NAME:Freak Strike- ABSOLOUTE EPISODE NUMBER:104- RESOLVED EPISODE NAME:Freak Strike-
SEASON:S06- EPISODE:E03-
##############LISTING FOLDER PERMISSIONS#################
ORIGIONAL FILE>ls -l /var/lib/mythtv/recordings/1037_20091203193000.mpg
-rw-r--r-- 1 mythtv mythtv 1181192192 2009-12-03 20:00 /var/lib/mythtv/recordings/1037_20091203193000.mpg
BashSExx WORKING DIR>lsmod -l ~BashSExx/South Park/
total 264
-rw-r--r-- 1 mythtv mythtv   4495 2009-12-08 21:57 South Park.Ename.txt
-rw-r--r-- 1 mythtv mythtv    525 2009-12-08 21:57 South Park.E.txt
-rw-r--r-- 1 mythtv mythtv    490 2009-12-08 21:57 South Park.S.txt
-rw-r--r-- 1 mythtv mythtv 253693 2009-12-08 21:57 South Park.xml
EPISODE INFORMATION: South Park Freak Strike = S06E03
VERIFIED FOLDER: /mnt/NAS/Video/shows/South Park
ATTEMPTED MOVE:/var/lib/mythtv/recordings/1037_20091203193000.mpg
TO:/mnt/NAS/Video/shows/South Park/South Park.S06E03 (Freak Strike).mpg
@@@@@@@@@@@@@OPERATION FAILURE Tue Dec 8 21:34:51 CST 2009 @@@@@@@@@@@@@@@@@
```

---

### Post by sgosnell on 2009-12-08
You have to be root to change those directories.

---

### Post by outleradam on 2009-12-08
I'm just trying to move /var/lib/mythtv/recordings/1037_20091203193000.mpg  WHY WOULD I NEED TO BE ROOT?


How can I get mythtv to do that? I don't understand the permission thing.  mythtv is the owner and the group, it has rw access as owner, why won't it move the file?

These are the only relevant lines:
ATTEMPTED MOVE:/var/lib/mythtv/recordings/1037_20091203193000.mpg
TO:/mnt/NAS/Video/shows/South Park/South Park.S06E03 (Freak Strike).mpg
@@@@@@@@@@@@@OPERATION FAILURE Tue Dec 8 22:08:01 CST 2009 @@@@@@@@@@@@@@@@@

---

### Post by outleradam on 2009-12-08
I changed permissions to 777 and mythtv still cannot move files.  wtf?

---

### Post by sgosnell on 2009-12-09
First, I have no clue about MythTV, whatever that is.  But in general in Linux, you have to be root to remove files from anywhere but your home directory, and moving involves deleting files.  You can copy from the filesystem, but not delete.

---

### Post by outleradam on 2009-12-09
I'm not root.  I can do it from the shell, but when I try to do it from a script as a myth tv job it fails!

---

### Post by teward on 2009-12-09
we understand what you're saying.  What WE'RE saying is that you physically have to be root to move files.

Now, have you tried running the Bash script with the command ```
sudo
``` before it?  That might make it work.

---

### Post by cariboo on 2009-12-09
Are you running the script as the mythtv user, or as a regular user? If you are running the script as a regular user, add the user to the mythtv group:

```
sudo gpasswd -a <usernme> mythtv
```

This should solve your problem.

---

### Post by Mister.Vash on 2009-12-09
This might be better served if it was moved to the mythbuntu section
[http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)

I'll make the assumption that you are invoking the script via a Myth Job?  If so, then the script would normally be running under the authority of the mythtv account.  I would check the permissions on the destination folder /mnt/NAS/Video/shows/South Park to make sure that the mythtv account can read and write to it.  If you see anything wrong with the directories permissions, then correct those and try again.  If you don't see anything odd, try opening a command shell as the mythtv user
```
sudo -u mythtv bash
```
then make sure you can navigate all the way into that folder and then  write a file and delete it as a test.  

You also mentioned a notify-send for that script - kind of hard to say what might be wrong with that without actually seeing the script.  Could be that the user isn't allow to do it, or isn't allowed to read some configuration files - hard to say

---

### Post by outleradam on 2009-12-09
So mythtv does not have access to run the mv command or the notify-send command?
 
I am running Ubuntu 9.10.  I guess I need to figure out how to list permissions and change permissions for users from the terminal.   How can I do that?

---

### Post by outleradam on 2009-12-10
ok, it turned out to be a privilege issue. So, for the 2nd part, why won't this line execute in the script 

notify-send "MythSExx" "Error moving $3 to $MoveDir/$ShowFileName" -i "error"

Does notify-send require privileges?  How can I increase the privileges of a user which is not listed in the GUI?

---

