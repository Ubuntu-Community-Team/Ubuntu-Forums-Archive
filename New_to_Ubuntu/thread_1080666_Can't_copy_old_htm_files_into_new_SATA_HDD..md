---
title: "Can't copy old htm files into new SATA HDD."
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Han Solo on 2009-02-25
I just got ubuntu yesterday. I previously had a problem having vista recognize an old ide drive. So I decided to use ubuntu to copy all files from that drive into my partitioned SATA drive. After I copied and paste it the OS asked to skip some files which I did. I noticed that the files were old html file folders. I kept skipping them until it started to copy some other bigger folders which I know had no html file folders and it asked me to skip them anyway. What can I do? Should I maybe use an older Linux based OS in order to recognize these files? I am completely new to all of this.

---

### Post by sleepyjon on 2009-02-26
Why did it say it wanted to skip them? It's hard to help you without more information.

---

### Post by northern lights on 2009-02-26
You should be able to copy any sort of file with nautilus (gnome file manager). In order to get a decent error message, could you please attempt to do the copying from the commandline?

Please open a terminal (Gnome Menu: Applications > Accessories > Terminal) and run (type in and hit Enter key)```
cp /path/to/source /path/to/destination
``` where the two paths obviously need to be replaced by your specific paths (as shown in the nautilus location bar). Unless the copying goes flawless, please post the output here (Copy/Paste into thread, enclose in code tags (hash/pound/# button ontop).

Thank you.

---

### Post by Han Solo on 2009-02-26
I am not too familiar with this type of command line. I can't seem to copy and paste the path because there is no apparent path bar being displayed as is present with windows.

---

### Post by northern lights on 2009-02-26
The path you can see in nautilus by default. If you're still unsure, navigate up until you reach the root filesystem (/) now go back to your specific location - it's probably something along the lines of from /media/deviceXY/folder to /home/USER/folder. And then just type```
cp /source/path/ /destination/path
``` into the terminal and hit Enter. The mouse highlights, Ctrl+Shift+C copies (or Edit > Copy) from the terminal's menu.

---

### Post by Han Solo on 2009-02-27
This is what what I typed into the terminal cp /source/media/*******/*****/ /destination/media/DRIVE_D/******* B and after pressing enter the terminal states "cp: target B is not a directory. Perhaps I should rename the folder because I think the problem may lie on long path names. And thank you for all the help so far.

---

### Post by Fenris_rising on 2009-02-27
J had something similar to this in that files saved to my SDHC card with 8.04 could not be moved into the replacement file system of the newly installed 8.10. The solution for me was to change the permissions of said files. All was well once I had done this. Hope that may help you.

regards

Fenris

---

### Post by northern lights on 2009-02-28
> **Han Solo said:**
> This is what what I typed into the terminal cp /source/media/*******/*****/ /destination/media/DRIVE_D/******* B and after pressing enter the terminal states "cp: target B is not a directory. Perhaps I should rename the folder because I think the problem may lie on long path names. And thank you for all the help so far.

Did you run the above verbatim? Cause if so, I think you still just got the paths wrong. I didn't mean to literally make you type "/destination/...". "/source/path/" or "/path/to/folder/" are all just placeholder names. The syntax of *cp* is *cp -OPTIONAL_FLAGS SOURCE_PATH DESTIONATION_PATH*. For the current purposes, no flags need to be set. So let's assume you want to copy something from a partition mounted as "Partition2" in "/media" to a folder called "Folder1" in your home folder and your username were "HanSolo". Then the correct command would be ```
cp /media/Partition2/ /home/HanSolo/Folder1/
```make sure the destination has been created in advance, either via the file manager or```
mkdir /home/HanSolo/Folder1
```

Invoking cp from the terminal bears the advantage that you can copy/paste exact error messages in here. If you're unsure about the paths, precisely describe what you want to move from where to where - we'll get it done.

Note, that if you want to copy into somewhere outside /home you might have to take care of permissions. All your internal partitions should ideally be mountes as read/write, but maybe they're owned by root or the like. If you can't write into a location, because you don't have the permissions to do so, ask yourself whether permissions are badly set or whether the location might just not be ideal. It is advisable to not use your rootfilesystem (/) or system folders (/apt /etc /younameit) for file storage. If a location in /media or /mnt does not belong to you, you can change ownership and/or permissions via either the *chown* and *chmod* commands or the filemanager.

Via the filemanager:
Right-click on a certain location, choose "Properties" - Permissions are found under the third tab. If it's greyed out or unchangeable for you, open nautilus as root via```
gksu nautilus
```Then you will be able to do the required operations.

Via chmod/chown:
If you're not very comfortable with the commandline, it might be more advisable to go the filemanager route, but still, you can check [man chown]("http://www.manpagez.com/man/8/chown/") and [man chmod]("http://www.manpagez.com/man/1/chmod/")

---

