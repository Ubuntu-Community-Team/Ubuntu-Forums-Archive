---
title: "Files System  Drive Size problem"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by rikilshah on 2009-12-20
I have triple boot with WinXP,Win7 and Ubuntu 9.10.I have installed  ubuntu using wubi in Win7.Now the problem is I have specified Ubuntu only 10 GB and currently I am running out of space.The Drive on which Ubuntu is installed is of 14.5 GB.I have two another empty drives of 50 GB each.So My question is,Is it possible to stretch File System drive? Is there any other way to overcome this problem?

---

### Post by oldfred on 2009-12-20
I have always considered wubi as a test install just to see if you like it. It is faster than the liveCD but has all the issues of being inside windows as a program. Any windows corruption will cause Ubuntu to fail also.

It is time to install Ubuntu onto one of your other drives as a dual boot. If you can easily select drive order in BIOS, set the new drive to first and install Ubuntu to it. Your current drive will remain the same and if made first in BIOS again will work as it does now. Even if it is older and has older ide drives that require changing the order inside the computer it would be worth switching. Then when the new install is working well you can delete the wubi install.

---

### Post by rikilshah on 2009-12-20
Yes,I got you.but my point is I want to keep my current installation as it is.:(

The other way can be Is there any way that I can make a CD/DVD which contains my current system and after that I'll follow your instruction.....So I can retain my current installation.
It is same as Recovery Disk I think so.I have came across one tool called Remastersys but i can't use it as my file system size lesser than its requirement.:confused: :( 

I think you got my problem....

---

### Post by oldfred on 2009-12-21
The key files to save all all in /home. This is why for many new installs they recommend an additional separate partition for /home so you can do a clean install and keep your files and the hidden files that are your settings. I am not sure if any settings anywhere else would carry over since wubi is inside windows anyway.

I would backup/copy /home and new a new install then copy the data from your backup into the new install.

---

### Post by rikilshah on 2009-12-25
I found Sbackup which does same thing you stated.Thanks for your reply!!

---

