---
title: "Trouble mounting usb flash drive from command-line"
date: 2010-04-03
forum: New to Ubuntu
---

### Post by beetlemeyer on 2010-04-03
Hello - I'm having some trouble mounting a jump drive from the command line.  I've googled for a solution but had no luck so thought I'd ask here.

when I plug it in I see 
[ ... ] sd 3:0:0:0: [sdb] Assuming drive cache: write through

If I run sudo mount I do not see it mounted anywhere, so I do:
sudo mount /dev/sdb

mount: can't find /dev/sdb in /etc/fstab or /etc/mtab

So I try:
sudo mount -t usbfs /dev/sdb /media/Lexar
cd /media/Lexar
ls

I get:
001
devices

I tried mounting as vfat, ntfs, and msdos - none work.  A little confused what I'm doing wrong.  Thanks in advance for the help.

---

### Post by atomizer on 2010-04-03
You need to mount the partition on it, not the drive itself

so a ```
sudo mount /dev/sdb1 /media/Lexar
``` should do the trick.
(if you have the folder /media/Lexar offcourse)

---

### Post by beetlemeyer on 2010-04-03
That did the trick, thankee

---

### Post by beetlemeyer on 2010-04-03
So the filesystem is being mounted as root now.  Is there any way I can mount it so that my normal user can have write access?

---

### Post by beetlemeyer on 2010-04-03
n/m, added a line to fstab and got it working.

---

