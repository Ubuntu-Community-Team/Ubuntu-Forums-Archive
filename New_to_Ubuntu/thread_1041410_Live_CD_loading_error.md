---
title: "Live CD loading error"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by artoo36 on 2009-01-16
Hey, I am new to Ubuntu and would really like to get the pig rolling.
Yesterday I downloaded the .ISO file and burnt it to disk, following the instructions on the website (by the by, I am trying to install 8.04).
When I tried it out on my computer, however, I got a line of text:
ISOLINUX 3.53 Debian-2007-12-11 Copyright (C) 1994-2007 etc. (the etc is mine)
It sits there for a minute and then says:
Disk error 80, AX=4200, drive 9F

Did I do something to mess up the process, or did I grab the wrong version? I think I picked up the 64 bit, because I am running dual Athlon 64X processors and I have heard that dual cores allow for 64 bit, as does Athlon 64 processors... 
Vista says it is a 32-bit system, but I don't know if it is referring to itself or the computer.

I am running a Compaq, if that makes any difference...

Thanks!

---

### Post by joshp93 on 2009-01-16
Try using Wubi to do it, if your wanting to dual boot.

---

### Post by wilbbe01 on 2009-01-16
You can have a 32 bit os (your Vista) even with 64 bit processor(s).  I would suggest trying 8.10 instead of 8.04 as it is newer and likely would have better support for different hardware.  You might also try the option for the "alternate" install disk when downloading the iso from the downloads page.  How old is your computer and what model is it?

---

### Post by artoo36 on 2009-01-16
It is a brand-new Compaq Presario SR5710F.

I had considered just using the newest version, but I had heard that it was a little bit buggier and more coding intensive. I am not quite a novice, but the peak of my knowledge/skills was on Win 98... nowadays I'm pretty much a noob-who-fancies-himself-geek. :)

I might just give the newer version a try, though... 

What is wubi, exactly?

---

### Post by gettinoriginal on 2009-01-16
Here is a wiki on wubi  :P
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by wilbbe01 on 2009-01-16
Or here.  I personally do not like wubi.  Why make things more complicated than they ahve to be?  I like the two separate as possible which makes troubleshooting problems when they arise a whole lot simpler.  That is just my opinion though, I'm sure there are people who swear by wubi.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by artoo36 on 2009-01-16
Just checking... Wubi won't damage my instillation of Vista at all, will it?
The computer came with a pre-instillation, but no recovery disks or anything... I will back up everything I can, but I would don't know to what extent I can do anything like that.

---

### Post by gettinoriginal on 2009-01-16
If you do not have a recovery disk for Vista, I advise a dual boot as here:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by artoo36 on 2009-01-17
All thsese suggestions are great, but they require a functioning disk.
I tried the disk on a different computer and it doesn't work there either.

I now have restore disks for vista, so should I use wubi? Will it work with a disk that won't load?
Or do I need to go buy another disk and try again?

(I only have dial-up at home, so I am trying to see if there is any way I can fix this without spending another day running around town to get all the peices together)

---

### Post by gettinoriginal on 2009-01-17
Since you are on dial up, may I suggest you go to [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) and request a free CD.  Yes, you will have to wait, but you will have a functioning disk that works, and you can either wubi or dual boot.  We look forward to having you with us in ubuntu, and wish you good luck whatever your choice :P

---

### Post by artoo36 on 2009-01-18
I got it! The first time I used InfraRecorder on a high speed writer.
I retrieved the image from the first computer on my flash drive and re-wrote it using ISORecorder on an older computer with a slower drive.

Thanks for all your help!

---

### Post by artoo36 on 2009-01-18
Oh... How do I mark a post as solved?

---

### Post by gettinoriginal on 2009-01-18
Because of all the database problems lately, the solved selection has been temporarily disabled.  Glad you got it fixed. :P

---

