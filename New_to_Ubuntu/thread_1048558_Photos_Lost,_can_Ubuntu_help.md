---
title: "Photos Lost, can Ubuntu help?????"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by eroom on 2009-01-23
I hope you can help yet another stupid person. I failed to back up pictures and now my hard drive has gone down.

My course of action so far has been to remove my drive put into another desk top and have it as a slave drive.My thinking was to transfer photos onto master drive.

Whenever I attempt to do something with slave drive it asks for it to be formatted.I am fearing the worst and think all data has been lost.

Do you think it would be possible to put Ubuntu onto the hard drive and retrieve photos that way. Apologies if this is a really stupid question.

Thanks in advance.

---

### Post by Muffinabus on 2009-01-23
You can try without installing Ubuntu.  Just download the live cd .iso, burn it, and boot up from the CD Rom and see if you can access the drive through the live CD.

---

### Post by OffAxis on 2009-01-23
No!
The first rule of salvaging data:
**NEVER write anything to the hard drive in question.**

You can try booting from an Ubuntu liveCD and see if it can read it.

You can try the ultimate boot cd ([http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")) and see if one of it's utilities can read from it (see the Hard Drive Diagnostics section).

Question: does your bios detect the right size and type of hard drive?

If it doesn't have a physical defect, it may just be the file structure that's been scrambled, which you may be able to rebuild.
If I remember correctly, at the end of the Master Boot Record Windows puts a copy of the data it needs, so you may be able to manually rebuild it.

You can read up on it here:
[http://en.wikipedia.org/wiki/Master_Boot_Record]("http://en.wikipedia.org/wiki/Master_Boot_Record")

---

### Post by sully101 on 2009-01-23
Photorec is the program you want to recover lost files. It can be installed by 

sudo apt-get install photorec

or 

sudo apt-get install testdisk

---

### Post by eroom on 2009-01-23
Sorry, I forgot to mention XP was installed previously!

---

### Post by mkvnmtr on 2009-01-23
Don't do anything to disturb the disk in question. Go to another computer and download one of the live disks on the live disk page. I keep system rescue and parted magic and some others. Look for a system that has the tools to recover what you want. None of them are big downloads. Burn the one of your choice and boot your computer with the live disk. Fund the app that you want to use to retrieve your files and the gui should explain how. If it doesn't come back to the forum to ask if someone has experience with that app. The guy that said to download a program to your system did not understand what has happened.

---

### Post by eroom on 2009-01-23
Thanks for all your responses, I'll give the last one a try.

---

