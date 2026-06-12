---
title: "please help, 0mb drive"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by mvthai on 2010-02-17
Hi, I am new to ubuntu and I tried to run it, thinking it was like a live cd where I can run it from the cd itself but when it tried to install on my drive, I cancelled out. But now my drive is seen as 0mb, unreadable, unknown drive under windows. I have some data on it that I can not loose. I think when I ran ubuntu, it wrote to my drive and messed up the tracks or got corrupted. Please help. Any advice on how to get the drive back on my windows os? Thanks in advance.
 
Mike

---

### Post by ubunterooster on 2010-02-17
sounds like you fomatted your drive :'(  To get to be able to use this drive reformat it to NTFS or FAT. (Data will be difficult to recover esp. concerning time) i think the disk utility for windows is under accessories/ system tools.

---

### Post by Satoru-san on 2010-02-17
did you click install or "try without changes to my harddrive" ?

if the latter, then your harddrive is fine, if not, you may have overwritten your windows. And AFAIK there is no way to recover easily. You cant just click undo.

---

### Post by mvthai on 2010-02-18
No, I started running ubuntu and when I realized that it was asking for a place to install ubuntu, I cancelled out.  I don't think I installed anything but it did do something to the drive because now, it's not seen correctly by windows.  Under windows, it sees the drive as "unknown, unreadable, 0mb" and there are no options to bring the drive online, convert, etc.  
Also, under the bios, it also sees the drive as defunct, 0mb?  Could this be a result of ubuntu writing to the harddrive tracks somehow and corrupted something on the tracks where the firmware is or where it reports the drive?  If so, is there any way of recovering from that?  Thanks in advance.  All help appreciated.

---

### Post by theozzlives on 2010-02-18
Ubuntu has no effect on how your BIOS recognizes the drive. If you can, boot the live CD (Run Without Changes), go to Applications > Accesories > Terminal and post the output of
```
sudo fdisk -l
```
that's a lowercase L, not a 1.

---

