---
title: "External Hard drive is Read only"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Wyrm780 on 2011-02-21
I have an 250 external hard drive that I'm using for just about everything. My windows system is very old and has a 60 gig hard drive and my linux netbook has a hard drive problem so its running off a 10 gig SD card. I can read and write to the hard drive just fine on my windows, but when i plug into my netbook its read only. I've tried to change permissions by right clicking and chmod but when I right click and go into properties -> Permissions and attempt to change it says "Sorry, could not change the permissions of "AQUILLO": Error setting permissions: Read-only file system"
as for chmod it says "chmod: changing permissions of `AQUILLO': Read-only file system" but doesnt change anything.
Please note that I'm pretty much a newbie at Linux.
I'm running "Aurora" eeebuntu 4
The External Hard drive is in ntfs format and I want to avoid reformatting (especially since I cannot backup the files since neither of my computers have enough space)

---

### Post by mikewhatever on 2011-02-22
That error means that the file system is mounted as read only, which usually happens because of file system errors. Try running a check on that partition in Windows.

---

### Post by Wyrm780 on 2011-02-24
Well I tried fixing the partitions to no avail. I backed up the necessary files on a flash drive and reformatted but it still wouldn't work. In the end I had to reformat it on my Linux then use chown to change the owner from root to myself. Thanks for the suggestion though.

---

