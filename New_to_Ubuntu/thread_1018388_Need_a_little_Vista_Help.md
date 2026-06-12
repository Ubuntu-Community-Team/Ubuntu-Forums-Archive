---
title: "Need a little Vista Help"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by CPrider2009 on 2008-12-22
I've decided to give Ubuntu a shot (after having horrible problems with Windows XP and Vista) and I have come to a road block in installation with Ubuntu.  Here's my set up:

Intel Core 2 Duo 2.13 Ghz
2 Gb of RAM
a 250 GB SATA Hard Drive (Currently Vista which I would like to keep for right now)
a 60 GB IDE Hard Drive (What I would like to put Ubuntu on)

I have read some of the other posts on how to set up a SATA+IDE configuration, but those didn't help.  Everything is installed, but when I boot back up, I come to the Windows boot up rather than Grub and it says that the winboot file is missing.  If any of you could help me that would be great!

---

### Post by igknighted on 2008-12-22
> **CPrider2009 said:**
> I've decided to give Ubuntu a shot (after having horrible problems with Windows XP and Vista) and I have come to a road block in installation with Ubuntu.  Here's my set up:

Intel Core 2 Duo 2.13 Ghz
2 Gb of RAM
a 250 GB SATA Hard Drive (Currently Vista which I would like to keep for right now)
a 60 GB IDE Hard Drive (What I would like to put Ubuntu on)

I have read some of the other posts on how to set up a SATA+IDE configuration, but those didn't help.  Everything is installed, but when I boot back up, I come to the Windows boot up rather than Grub and it says that the winboot file is missing.  If any of you could help me that would be great!

Try switching the boot order in your BIOS to whichever HD is not currently first.

---

### Post by bumanie on 2008-12-22
From a live ubuntu cd Go to terminal and post the output of code > sudo fdisk -l

---

### Post by CPrider2009 on 2008-12-22
Okay, I have given EasyBCD a try.  What I need help is to set up my boot up in NeoGrub.  How do I do that?

---

### Post by CPrider2009 on 2008-12-22
And I've tried switching the hard drives.  It gave me a boot error.

---

### Post by CPrider2009 on 2008-12-22
Okay, I now have grub running, but I don't know how to start up Ubuntu now.

---

### Post by Zeedok on 2008-12-22
> **CPrider2009 said:**
> Okay, I now have grub running, but I don't know how to start up Ubuntu now.

If you have GRUB running, you should be able to choose your Ubuntu OS.  What exactly is happening??

EDIT:

[This might help as well]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), if you haven't already tried it.

---

### Post by CPrider2009 on 2008-12-26
Okay, I have Ubuntu up and running on my second hard drive, but in order to run it I have to go through my BIOS and switch my boot-up drives around.  Is there any shortcuts around this or is this the way I'm going to go from.

---

