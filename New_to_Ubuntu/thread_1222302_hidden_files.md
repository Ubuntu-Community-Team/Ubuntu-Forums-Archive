---
title: "hidden files"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by 007casper on 2009-07-24
I am editing files bunch of files. In every edit, I get a hidden file.  As far as I know hidden files are suppose to be like back up files.  I dont need them.  

How can I get rid of them? What are the cons and pros of deleting them?

---

### Post by Whiffle on 2009-07-24
Hidden files are not backup files, they usually (almost always) hold configuration settings.  So if you delete them, your configuration settings reset.

---

### Post by LookTJ on 2009-07-24
Most hidden files and folders in your home folder are your preferences and settings when presented with a ".name".  Unless presented with a ~, that's a backup file of the original(gedit does this I believe)

---

### Post by michy99 on 2009-07-24
The backup file will have the same name as the edited file with a ~ on the end. To see all the hidden backups in a directory:```
ls *~
```To delete them:```
rm *~
```

---

### Post by michy99 on 2009-07-24
Also, if you don't want gedit to make a backup when you edit, go to Edit->Preferences, click on Editor tab, un-check 'Create a backup copy when saving.'

---

### Post by danggrianto on 2009-07-24
FYI... backup will save your live someday.. LOL

---

### Post by 007casper on 2009-07-24
awesomeneesssss! Also, thank you so much for the gedit editor preferences tab.  

rm *~ 

I have bunch of files with lots subfolders/directories.  If I go to the main directory in the terminal, and rm *~ 

will that take care of subdirectories? 
or thats just for the current directory and wouldnt include any other directory.

---

### Post by PGScooter on 2009-07-24
check out the man page for rm, it will tell you have to have it search in subdirectories:

```
man rm
```

be careful with recursive rm. I would not do it.

---

### Post by 007casper on 2009-07-24
I checked out man rm... 

why wouldnt you do it?

---

### Post by XCan on 2009-07-25
Because if you do it wrong, you're screwed.

---

### Post by Whiffle on 2009-07-25
> **XCan said:**
> Because if you do it wrong, you're screwed.

Or, you delete more then you intended.  Alot of times you can replace "rm" with "ls" and it will give a decent preview of what is going to be deleted.

---

### Post by lukjad on 2009-07-25
> **007casper said:**
> I am editing files bunch of files. In every edit, I get a hidden file.  As far as I know hidden files are suppose to be like back up files.  I dont need them.  

How can I get rid of them? What are the cons and pros of deleting them?
It's not worth it to delete hidden files for two reasons.

1) Usually they are configuration files.

2) The backups are so small compared to disk size, they are not worth the trouble of deleting them, especially when you consider that should you ever need to revert to an older version of a file, if you delete the backups, you will have to recreate that file from memory, or from scratch.

---

### Post by sisco311 on 2009-07-25
I wrote a script to delete the *backup* files:
```
#!/bin/bash

# size of the window:
WIDTH="400"
HEIGHT="400"

# set this to FALSE if you don't want to auto-select the files
CHECK="TRUE"

# text displayed :)
TEXT="Select files..."

find ~ -name "*~" | sed "s/\(.*\)/"$CHECK"\n\1/" > /tmp/deltilde

IFS="
"

zenity --list --text "$TEXT" --column "Delete" \
--width $WIDTH --height $HEIGHT \
--checklist --multiple --separator "
" \
--column "File" $(cat /tmp/deltilde) | xargs -d "
" rm
rm /tmp/deltilde

exit 0

```
use it on your own risk. :evil:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122369&stc=1&d=1248542924[/IMG]

---

### Post by lukjad on 2009-07-25
Wow. I need to keep a copy of that, if just out of awe.

---

### Post by sisco311 on 2009-07-25
The script searches for backup files in the user's home directory and displays a list of the files. 

I've attached a screenshot.

---

### Post by 007casper on 2009-07-26
sisco311 thank you so much! Nicceeee!

Before your post, I just went to View > show hidden files then I sorted by type.  After that I deleted manually.  

I wish I had your tool before... however, it will be very handy in the future.  Also, it is really nice reference.

Thank you once again.

---

