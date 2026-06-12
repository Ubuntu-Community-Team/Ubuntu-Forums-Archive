---
title: "Error creating directory: No space left on device"
date: 2011-06-30
forum: New to Ubuntu
---

### Post by Populus on 2011-06-30
I have a load of files on a USB stick which are duplicated on an SD card. I've just added a couple of small files to the stick, which now shows as having 29.9GB of 32GB used. However, when I tried to copy the same files to the card, I received the message < Error creating directory: No space left on device >. The card contains exactly the same files. I deleted 6GB and still got the error message when I tried to copy the new files over, even though the card now shows as having only 26.3GB used out of 33GB. Why am I getting this message?  :confused:

---

### Post by drs305 on 2011-06-30
Welcome to the Ubuntu forums.

One reason may be that the deleted files are still in your Trash bin. The trash bin must be emptied before the space is freed up. Try right clicking the Trash Bin to see if emptying it solves your problem.

If it doesn't, open a file browser and look for a folder on your device called .Trash-1000 (or similar). Note it's a hidden folder. This contains deleted files as well. Inspect the contents, then you can delete it with SHIFT-DEL.

Here is a guide on other disk space issues that affect users and how to resolve them:
[http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")

---

### Post by Populus on 2011-06-30
Thanks, all OK now. I had a feeling the trash bin might have something to do with it - it does take an inordinately long time to empty when very full.

Populus

---

### Post by dFlyer on 2011-06-30
Please mark thread as solved.

---

