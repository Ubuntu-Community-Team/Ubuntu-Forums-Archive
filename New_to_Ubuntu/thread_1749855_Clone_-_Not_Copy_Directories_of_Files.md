---
title: "Clone - Not Copy Directories of Files"
date: 2011-05-04
forum: New to Ubuntu
---

### Post by grizzlybear62 on 2011-05-04
[FONT=&quot]I use multiple OS's so my computer has a drive cage connected to SATA1.  Each OS is on its own drive (for isolation).  For this discussion I am using Ubuntu 11.04 (upgraded from 10.10).  Also installed on the system is a 1TB Mega_Storage drive formatted in NTFS (for cross platform compatibility).  This Mega_Storage drive is common to all of my OS's.  I also have a 16GB flash drive (formatted in FAT32) which I use at work.  Most of the files on the flash drive are static, but a small percentage of them change.   Both drives are mounted (flashdrive - automagically & Mega_Storage - manually mounted).  Both drives have read and write privileges.   All files are owned by me and have default privileges (due to their use on Win32 platform).[/FONT]
  
  [FONT=&quot]Now on to the question &#8211;[/FONT]
  
  [FONT=&quot]I have a script on the Win32 side using a utility called 'XXCopy.exe' which will clone the contents of the flash drive to the Mega_Storage drive.  I would like the same thing on the Ubuntu side.[/FONT]
  
  [FONT=&quot]By clone I mean just that, the utility will check each file on the source (flash drive) against the destination (Mega_Storage drive).  If the files are identical, nothing is done.  If the source file is newer, then it over writes the destination file.  If extraneous files exist on the destination it will delete them, leaving me with an exact duplication of the flash drive (in case I need to reload for corruption reasons).[/FONT]
  
  [FONT=&quot]A simple cp -r -u -p does not do the job because it does not delete the files that exist only on the destination.[/FONT]
  
  [FONT=&quot]I tried rsync but that doesn't seem to work. Here is my script code :[/FONT]
  
  ```

  [FONT=&quot]#!/bin/bash[/FONT]
  [FONT=&quot]# Clones the Flashdrive to Mega_Storage Directory as a backup[/FONT]
  [FONT=&quot]rsync -v -r -t -W -e,delete /media/FLASH_DRV/* /media/Mega_Storage/Flashdrive/[/FONT]
  [FONT=&quot]wait[/FONT]
  
```  [FONT=&quot]Thinking that I might not have the necessary switches, I installed Gsync from the repository.  I ticked the necessary options and wound up with the same results.  The extraneous files on the destination were not deleted.[/FONT]
  
  [FONT=&quot]To give one a visual picture:[/FONT]
  
  [FONT=&quot]Source Dir Files = 1, 2 ,3[/FONT]
  [FONT=&quot]Destination Dir Files = 1, 4, 5, 6[/FONT]
  
  [FONT=&quot]The utility compares file 1 and finds that it is the same.  No action taken.[/FONT]
  [FONT=&quot]The utility should copy the source files 2, & 3 to the destination as they are new.[/FONT]
  [FONT=&quot]The utility should delete the destination files 4, 5, 6 because they do not appear in the source.[/FONT]
  
  [FONT=&quot]I have Google'd variations of Ubuntu, Sync, Clone Directory, & XXCopy, and have not found anything that pertains to my situation.[/FONT]
  
  [FONT=&quot]Any help would be appreciated.[/FONT]
  
  [FONT=&quot]Thanks [/FONT]

---

### Post by papibe on 2011-05-05
I have used the following options to accomplish what you want:
```
$ rsync -aP --delete /path/to/dir1 /path/to/dir2 
```
-a  will go recursively and also implies -rlptgoD
-P  is a nice way to get a report, since equals to --partial and --progress
--delete will delete the extraneous files.

I hope it helps.

---

### Post by jtarin on 2011-05-05
For what you want there is the cross-platform [AKG Backup]("http://www.akgupta.com/applications/akgbackup.htm")......you can specify how and where to back up. You must have Java installed. Very powerful and fast. Practice before commit. Been using it for about 3 years.....only screw-up was my own. Freeware with nag but author will register for free with an email.
After the first run, only the new or modified files are backed up leaving the unmodified files in the backup folder untouched, making the backup process very fast. Data compression is also an option. A number of backups of the same folder can be created, if backup is being done on the disk itself.

---

### Post by grizzlybear62 on 2011-05-05
Thank you papibe.  That does exactly what I wanted.  Nice touch on the report.  Let's me know what's going on.  Thank you also jtarin.  I may look into that for larger jobs like my quarterly backups to the off site hard drive I keep in my safety deposit box.

---

