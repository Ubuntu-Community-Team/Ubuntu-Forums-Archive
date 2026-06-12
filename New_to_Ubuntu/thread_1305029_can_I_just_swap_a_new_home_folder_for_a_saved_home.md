---
title: "can I just swap a new home folder for a saved home folder"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by kapi on 2009-10-29
Read about others partitioning a home folder and it sounds ideal but a little daunting not to mention not knowing where to start.

it occurred to me that maybe I could save my existing home folder to an external drive and then once 9.10 is installed simply transfer it to the system and over write the new one.

any ideas

---

### Post by winotree on 2009-10-29
That's the method I use all the time and it works fine on my small device.  It's certainly worth the attempt.

---

### Post by dvlchd3 on 2009-10-29
Just be careful if you copy via the command line.  There are several hidden directories in your home folder that are needed.  They contain settings for different applications.  You usually do NOT want to include these directories in your backup, and when you restore, you do NOT want to delete these directories, or overwrite them.

If you are copying graphically, you will not touch the hidden directories unless you have nautilus set to show hidden directories.  (Hidden directories are directories that start with a '.')

---

### Post by winotree on 2009-10-29
That sounds like good information **dvlchd3**.  I'm still new enough to Ubuntu, Linux and computers in general to be confident enough to move the file, intact, from my SDHC to a new install and back again.  Thanks for that input.  :D

---

