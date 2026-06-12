---
title: "Windows File Sharing"
date: 2007-01-25
forum: Networking &amp; Wireless
---

### Post by MasterOfMadmen on 2007-01-25
I am trying to run some files from my Windows PC on my Ubuntu laptop.  Everything is working fine on Ubuntu.  I had no problem mounting the directory and am able to browse the files and download the files I want.  However, I don't want to have to download each file.  Specifically, I am trying to access my MP3 collection on my desktop.  However, in order to play the files, I have to copy them over first.  Anyone have some suggestions on how I can get my MP3s to play directly over the network?

---

### Post by Ptero-4 on 2007-01-25
Try setting the samba share as playlist directory in your music player app.

---

### Post by MasterOfMadmen on 2007-01-25
I'm not quite sure I understand your suggestion.  I tried adding the music to several players, and I get the error that it could not read from the resource.  The files are located on a Windows XP machine.

---

### Post by akudewan on 2007-01-30
Hi,

This guy here is having a similar problem: [http://ubuntuforums.org/showthread.php?t=348493](http://ubuntuforums.org/showthread.php?t=348493)

You can use smbmount to mount the shares, and then they should play fine.

---

