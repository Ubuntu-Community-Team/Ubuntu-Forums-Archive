---
title: "I;m I going to have any problems doing this?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by lobes on 2009-03-11
I currently have intrepid 64bit running on my machine.  Will I have any problems installing intrepid 32bit to use as a dedicated media center on my hard drive to use along side 64 bit?   I was planning on installing it from the 32 bit live cd.   Anybody tried this?

or would it be more benefical to just run the 32 bit XBMC under chroot?

---

### Post by teamcoltra on 2009-03-11
Well my suggestion and someone can slap my wrist later for this if need be:
If the install is going to be for a media center... why not use mythbuntu? [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

---

### Post by wannadumpwindows on 2009-03-11
> **lobes said:**
> I currently have intrepid 64bit running on my machine.  Will I have any problems installing intrepid 32bit to use as a dedicated media center on my hard drive to use along side 64 bit?   I was planning on installing it from the 32 bit live cd.   Anybody tried this?

or would it be more benefical to just run the 32 bit XBMC under chroot?

I haven't done it myself, but in a dual-boot set-up, you should have no trouble at all.

As long as you use separate /home's you should be fine.

In a dual-boot, they're completely independent of each other, other than both being in grub, they don't even care about each other being there.

---

### Post by lobes on 2009-03-12
> **teamcoltra said:**
> Well my suggestion and someone can slap my wrist later for this if need be:
If the install is going to be for a media center... why not use mythbuntu? [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

well media portal is my open source media center prefrence but it runs on .NET framework.  I've looked at XBMC and mythbuntu and elisa but for what I want it for XBMC clearly takes the mark.  I'm trying to get some help from the XBMC forums and try using there SVN which apparently does work on 64 bit sometimes.  So mabey i wont have to install 32 bit. we'll see


thanks wannadumpwindows for the input.

---

### Post by Kareeser on 2009-03-12
Like wannadumpwindows says, there shouldn't be any problems _as long as you keep both installations separate_.

You can share swap files, since they don't ever boot up at the same time anyhow :)

---

