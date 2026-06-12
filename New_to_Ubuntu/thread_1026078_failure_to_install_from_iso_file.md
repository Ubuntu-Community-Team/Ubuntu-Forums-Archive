---
title: "failure to install from iso file"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Would Mouse on 2008-12-30
Dear All
I have not got Ubuntu going yet, my Current system has two separate hard disks C: and D: in windows jargon. C: has FAT32 file system and a working Win98 installation which I no longer use and this is where I would like to install Ubuntu.  D: has NTFS file system and Win2K which I am using at the moment and would like to keep. I have downloaded Ubuntu 8.1 iso file and copied it to a CD, when I boot from this CD and opt to install the Ubuntu logo appears, an orange banner sweeps back and forward, then a White X appears on a black background and nothing else happens. The caps lock and scroll lock lights on the keyboard are flashing.
Should I have converted my C: disk to ext3 filesystem before trying the installation, if so how do I do this?
Thanks for any help

---

### Post by Ubu2010 on 2008-12-30
> **Would Mouse said:**
> Dear All
I have not got Ubuntu going yet, my Current system has two separate hard disks C: and D: in windows jargon. C: has FAT32 file system and a working Win98 installation which I no longer use and this is where I would like to install Ubuntu.  D: has NTFS file system and Win2K which I am using at the moment and would like to keep. I have downloaded Ubuntu 8.1 iso file and copied it to a CD, when I boot from this CD and opt to install the Ubuntu logo appears, an orange banner sweeps back and forward, then a White X appears on a black background and nothing else happens. The caps lock and scroll lock lights on the keyboard are flashing.
Should I have converted my C: disk to ext3 filesystem before trying the installation, if so how do I do this?
Thanks for any help


I am a new user too, but when I loaded Ubuntu 8.10 from an iso disk everything went perfectly. I did not have to change the filesystem at all, Ubuntu did that automatically. I don't know what the problem is that is happening to you, but I do know that Ubuntu will take care of the filesystem change for you.

---

### Post by oilchangeguy on 2008-12-30
> **Would Mouse said:**
> Dear All
I have not got Ubuntu going yet, my Current system has two separate hard disks C: and D: in windows jargon. C: has FAT32 file system and a working Win98 installation which I no longer use and this is where I would like to install Ubuntu.  D: has NTFS file system and Win2K which I am using at the moment and would like to keep. I have downloaded Ubuntu 8.1 iso file and copied it to a CD, when I boot from this CD and opt to install the Ubuntu logo appears, an orange banner sweeps back and forward, then a White X appears on a black background and nothing else happens. The caps lock and scroll lock lights on the keyboard are flashing.
Should I have converted my C: disk to ext3 filesystem before trying the installation, if so how do I do this?
Thanks for any help

what are your system specs? cpu speed, amount of ram, and hard drive size. i doubt it has the power to run ubuntu.

---

### Post by cariboo on 2008-12-30
It looks like the LiveCD is not detecting your video adapter properly, have you tried starting in safe graphics mode to see if it will boot to the desktop. Press Alt-F4 at the LiveCD menu screen and select safe graphics mode and then continue on to the Try it First part of the menu.

This will not effect the installation in any way as the video drivers are not installed until the installation is finished and you have booted for the first time.

Jim

---

### Post by Would Mouse on 2008-12-30
CPU Athlon 64, 2.01GHz
Disk 1  42.9Gb
Disk 2  128Gb
RAM  1GB
Video card  Radeon 9200SE series

---

### Post by oilchangeguy on 2008-12-30
> **Would Mouse said:**
> CPU Athlon 64, 2.01GHz
Disk 1  42.9Gb
Disk 2  128Gb
RAM  1GB
Video card  Radeon 9200SE series

i based my statement on the fact your computer has 98, and 2000 on it. why would you be using these antiques? and yes your computer has enough power to run ubuntu. you might try the alternate cd.

---

### Post by &gt;:3 on 2009-01-01
update: I've tried installing it on Wouldmouse's computer, I've managed to install without any major problems on other laptops but this has me stumped. 

Upon booting from CD or trying to install, the computer gets as far as loading the ibex wallpaper, before removing it, to show the background colour (orange-ish) and then totally freeze. Upon freezing the capslock and scroll lock LED's start flashing. 

Memory check, and CD check worked fine. System specs appear to be sufficient so I've no idea why it doesn't work. 

Help?

---

### Post by mkvnmtr on 2009-01-01
If you are trying to install 8.10 look on the wiki for known bugs. I have not tryed to install 8.10 yet but I seem to remember a bug they were talking about. I might be wrong but I think it was something about mod probe and it is a simple work around.

---

### Post by mangcool on 2009-01-01
> **Would Mouse said:**
> Dear All
I have not got Ubuntu going yet, my Current system has two separate hard disks C: and D: in windows jargon. C: has FAT32 file system and a working Win98 installation which I no longer use and this is where I would like to install Ubuntu.  D: has NTFS file system and Win2K which I am using at the moment and would like to keep. I have downloaded Ubuntu 8.1 iso file and copied it to a CD, when I boot from this CD and opt to install the Ubuntu logo appears, an orange banner sweeps back and forward, then a White X appears on a black background and nothing else happens. The caps lock and scroll lock lights on the keyboard are flashing.
Should I have converted my C: disk to ext3 filesystem before trying the installation, if so how do I do this?
Thanks for any help
Maybe the problem is the cd or the cd burner that you used.

---

### Post by evilkastel on 2009-01-01
> Maybe the problem is the cd or the cd burner that you used.

Thats more likely. If possible download again the ISO and burn it again at the lowest speed possible.

---

### Post by blackmoons on 2009-01-01
Well, it's taken me a while to get back to blogging in 2005, given many other things that have taken priority or just flat out distracted me at the start of this year.
A very belated happy New Year to everyone, especially those who managed to make my first year of blogging so enjoyable and instructive.  Thanks to everyone who sent me a note (and my apologies if I wasn't able to get back to you sooner...I'm still catching up with email well into the start of 2005).  Joerg at conscientious, Stan at reciprocity failure, John at orbit 1 (who's always run one of the most thoughtful of "photo-a-day" photoblogs)...before I even started a blog, I could tell that he was someone who liked to think about photographs, and not just dump one a day out there), Luis and Antonio at flux + mutability and defocused respectively, Kevin at photorant and photopermit, Todd at Gallery Hopper, Stacy at the space in between...

---

### Post by lkraemer on 2009-01-01
Try burning the ISO again, but first check the MD5SUM against what
the md5sum file says it should be.  If the MD5SUM verifies the ISO
file you downloaded is good.  Burn as DAO (Disk at Once) and at
a slow speed.  Boot on the CDR and see if it works.  If not you
can download the Alternate Install CDR and use that.

If you are using Windows, there are MD5SUM programs that you can
download and use to verify the md5sum.

I always use K3B on Ubuntu 8.04 LTS.

lkraemer

---

### Post by Would Mouse on 2009-01-02
SOLVED
Thanks to all who have helped.  I did burn another 8.1 iso but this also did not work, then I downloaded 8.04 which did install, no idea why that should be!  I do not yet have internet or sound but that will give me something to play with for a while, I expect to be back with more questions before long
Would

---

### Post by Would Mouse on 2009-01-02
Hope I have worked out how to say solved?

---

### Post by methodmarvel on 2009-01-02
> **Would Mouse said:**
> SOLVED
Thanks to all who have helped.  I did burn another 8.1 iso but this also did not work, then I downloaded 8.04 which did install, no idea why that should be!  I do not yet have internet or sound but that will give me something to play with for a while, I expect to be back with more questions before long
Would

It'll probably be a video issue then - I have the same problem.

8.04 detects whether you can use compiz and enables it if you can, disables it if you can't.

8.10 just assumes you can - regression much?

---

