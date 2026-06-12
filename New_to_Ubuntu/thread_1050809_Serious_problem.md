---
title: "Serious problem"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-26
MY "SMARTY PANTS FRIEND" was trying to fix some broken dependencies on my ubuntu hardy heron and ended up i guess deleting importan packages or something that has corrupted my whole computer,,i cant go to the desktop anymore,,everything is messed up,,all i care about is RECOVERING my DATA if possible,,after that i want a full clean install of ubuntu,,what could i possible do??? i just want to back up all the files,,is that still possible???? i dont think there gone,,its just completely impossible to acces them...HELP HELP HELP PLEASSSEEEEE:(

---

### Post by Rolcol on 2009-01-26
Your files are not gone (unless they have purposely been deleted.  Removing packages wont remove their files unless the --purge setting is included).  You can boot up from the Ubuntu Desktop install CD and have access to your hard drive.  Just browse to where your files are and copy them over to external storage.

---

### Post by Muffinabus on 2009-01-26
Yes, don't do anything to the drive that has your files on them.  Boot up into the Ubuntu Live CD and you should be able to access the drive.  Backup everything you want to keep and you should be fine.

---

### Post by itsvan on 2009-01-26
oh ok thank you very much i hope this works

---

### Post by itsvan on 2009-01-26
ok i put in this cd i have that says ubunut 64 bit install,is that the same as the ubunut live one?? it gives me some options to isntall all this stuff,,but none say to boot off the disc? if so where an i get ubuntu live disc or whatver

---

### Post by clive littlewood on 2009-01-26
Hi

The disc you have is the live CD

You need to insert the disc before you boot your PC.

Make sure that the Bios is set to "boot from CD" in the boot list.

To access the boot list on initial switch on press the appropriate key, usually esc or F1 it will tell you which key to press.

Hope this helps

Clive

---

### Post by hyper_ch on 2009-01-26
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by itsvan on 2009-01-27
i keep on trying usign that cd,,but it taktes me to another screen,with on sign of letting me jsut boot ubunut of the disc, eveyrthing else is isntalling in difernt modes,text mode OEM? mode or somting,,all kinds of stuff,,but nothing to boot it of the disc,,the closest one is boot of first hard disk... help should i downlaod another one?

---

### Post by bwang on 2009-01-27
This page: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) has the download links for the LiveCD.

---

### Post by mkvnmtr on 2009-01-27
It looks like you have the alt install disk. That is not going to work you better not do anything with it. Make sure you get the LIVE DISK  for your machine. It will offer you the option to try Ubuntu without changing your computer. When you get booted on that disk you can come back to the forum to ask how to get your files off of the hard drive.

---

### Post by itsvan on 2009-01-27
thank you i will try this i hope nothign got messed up

---

### Post by cariboo on 2009-01-27
You could also try starting in recovery mode and reinstalling your desktop. At the grub menu chose recovery mode anf at the menu select drop to root prompt using the arrow keys. Once at the prompt type:

```
dhclietn eth0
```

to start networking if you have a wired internet connection, use wlan0 if you connect wirelessly. Next at the prompt type:

```
apt-get install ubuntu-desktop
```

the above command should install all the files needed to get back to your desktop. Once the files have been downloaded and installed at the prompt type:

```
reboot
```

with some luck, you should boot to your desk top.

Jim

---

### Post by itsvan on 2009-01-27
ok i finally got into ubunut through the disc,,now i want to back up some files,,ive noticed some wont let me becausde of a user restriciton,,what do i do,,i need to save asll thse files and want to isntall a fresh copy of ubuntu

---

### Post by itsvan on 2009-01-27
hi when i prompt down to longing in as root,,it asks me for a maintenance passowrd,,waht do i do??

---

### Post by itsvan on 2009-01-27
hi when i go to the root prompt it says i need a password? or press control d,but it prompts me back to the screen before? what do i do

---

### Post by handydan918 on 2009-01-27
Have you tried entering your password?

---

### Post by itsvan on 2009-01-27
yessss

---

### Post by handydan918 on 2009-01-27
> **itsvan said:**
> yessss

AAnnnddd???










:D

---

### Post by itsvan on 2009-01-27
and it doesnt do anything it doesnt seem to work,,it prompts me back to the screen before it? what do i put instead,,

---

