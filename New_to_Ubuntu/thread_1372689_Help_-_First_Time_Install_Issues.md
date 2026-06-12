---
title: "Help - First Time Install Issues"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by ColonelKurtz on 2010-01-04
[FONT=Verdana][SIZE=2]OK - I am a total numb on Ubuntu or Linux for that matter so please have patience. I installed Ubuntu on this Dell Demension 8400 (5 years old) machine on Saturday after getting tired of my XP hanging.

The issues that I have encountered and still face are:

1 - installation
I was not able to install directly from the Ubuntu CD I made from the boot menu. I get to the main Ubuntu install screen but after that it just hangs on a blank screen and says something about a live install file not found. So I got Ubuntu installed (using same cd) by starting the install from within XP which resulting in my current dual boot. I would like  a clean (non-dual boot install).

2 - from within Ubuntu  I do not see my dvd drive. Its a 
[/SIZE][/FONT][FONT=Verdana][SIZE=2]Philips DVD+RW DVD8601 and I have no idea how to fix that.

3 - Even though I set my language preference to Canada English the Shift characters on my non letter keys are wrong. For example, when I try to type a question mark I get É.

I know that getting item 1 resolved will cause the fixes for 2 and 3 to be lost but I want to make sure I can get this OS working properly before switching from XP for good anyway.

Any help would be welcome...

Thanks
[/SIZE][/FONT]

---

### Post by bodhi.zazen on 2010-01-04
Sounds as if you performed what is called a "wubi" install.

There is not a new user friendly method of converting wubi to a "normal" install.

I would check your iso file and CD for errors (md5sum)

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You will need to boot the Ubuntu CD and install from there. 

How much RAM do you have in that machine ?

You may have better luck with the so called "Alternate" CD as the installer is more robust =)

---

### Post by Miljet on 2010-01-04
1. It sounds like you have a bad install disk. Did you check the disk for errors? The disk worked using WUBI because most of the required files are downloaded from the internet with that method.

2. Where exactly are you expecting to find your DVD drive? Normally it doesn't get mounted until you insert a disk. Then an icon for it should pop up on your desktop. You should also be able to see it by selecting Places->Computer.

3. That sounds more like a keyboard layout error than a language error. Go to System-> Preferences-> keyboard and select another keybaord layout.

---

### Post by ColonelKurtz on 2010-01-04
Thanks for the help.

bodhi.zazen:
I followed the hash comparison instructions on [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

The hash of my ISO file matched the hash for the download:
8790491bfa9d00f283ed9dd2d77b3906  =  ubuntu-9.10-desktop-i386.iso


I compared the iso file from the backup of it I put on my external HD which I originally used to burn the install cd as of course I cant view the cd without rebooting into XP first since my cdédvd player is out of action in Ubuntu.



I have a gig of RAM


What alternate cd are you referring to. Where can I get it.



Miljet:


1 - Please see note above on the hash compare. If I understand the how to it appears my original iso image is good although I guess the cd could be bad. I will boot into xp and try to create another then try to reinstall from boot menu.


2 _ I assume I would see the drive somewhere under Places but I dont. I tried putting in a music cd and still no joy.


3. I went to System - Preferences - Keyboard and tried a bunch of the Dell keyboards with no change. Here are some examples of the wrong keys:


question mark: É
at sign: "
number sign: /
dollar sign: $


My theory was that the undetected dvd drive was the reason the install didnt work.


thanks again for your help

---

### Post by Miljet on 2010-01-04
In addition to the hash check before burning the CD, when you first boot the install CD, you will find a  menu entry called "Check CD for defects." It takes a a while to run but will verify that you have a good burn.

As for the keyboard problem, try selecting a "generic 105 key" keyboard and see if that helps. If not, I am fresh out of ideas. Could be that you do indeed have a defective install. They give all kinds of weird problems.

---

### Post by bodhi.zazen on 2010-01-05
The keyboard is not as problematic, you can change it

[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

You may obtain the alternate CD from the downloads page or from one of the mirrors

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

Or from any of the mirrors

[http://mirrors.rit.edu/ubuntu-releases/9.10/](http://mirrors.rit.edu/ubuntu-releases/9.10/)

Alternate mirrors are listed at the bottom of the first link I gave you.

---

