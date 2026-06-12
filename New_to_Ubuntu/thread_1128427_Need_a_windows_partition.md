---
title: "Need a windows partition"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-04-17
I am going to need a small partition for windows on my xubuntu machine for messenger since pidgin doesn't get me see cams in yahoo. (I would use vmware but my computer is a celeron R with 1.5 gigs of memory.)

How do I install windows when I already have xubuntu on my machine without deleting anything?

---

### Post by Tim Sharitt on 2009-04-17
If you have some free space on your hard drive, you can boot a live CD and use gparted (partition editor) to shrink your Xubuntu partition enough to make room for Windows. Just be sure to back up your important documents and files, just in case problems are encountered.

---

### Post by LunaticHiatus on 2009-04-17
will windows know to install on my empty partition I specify in gparted? or will it try to install over my xubuntu partition?

---

### Post by etali on 2009-04-17
Windows will ask you which partition to install to when you start the setup process.

---

### Post by LunaticHiatus on 2009-04-17
ok, thanks, I just wanted to double check before I did anything

---

### Post by Elegia on 2009-04-17
Windows will probably overwrite grub though. To restore grub afterwards, take a look at [this guide]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by Ms_Angel_D on 2009-04-17
Just wondering if you tried amsn, It has a webcam feature that works quite well, and is in the repo's. Also Kopete is said to support yahoo's webcam feature, you may want to look into those both before you go through the trouble of setting up a whole other partiton simply for messaging.

---

### Post by SentientFluid on 2009-04-17
Stick with Pidgin a little longer and you won't need Windows just for webcam.

[http://blog.caseyho.com/2009/04/voice-video.html](http://blog.caseyho.com/2009/04/voice-video.html)

While waiting try out aMSN or Kopete...

---

