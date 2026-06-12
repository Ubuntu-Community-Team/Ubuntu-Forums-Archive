---
title: "Samba with PCs not always powered on"
date: 2006-11-10
forum: Networking &amp; Wireless
---

### Post by jeff777 on 2006-11-10
I'm having problem with Ubuntu getting cranky when I power down a computer it has a mounted smb share on. 

I have a small home network with three PCs sharing files via samba/smb.  One runs XP home; I turn it off when I'm not using it.  The second is an Ubuntu server that I leave on all the time.  The third also runs Ubuntu but is turned off every night.

I have setup fstab on the Ubuntu machines to mount the various smb shares on boot, and things are working OK.  The problem is that when one of the machines is turned off, the Ubuntu machines keep looking for the missing smb share.  They run very slowly and dump errors about CIFS to the console.

This continues until I power the other machine back on or until I umount the missing share with umount -l.  The Ubuntu machines slows to a crawl and are unusable while they're looking for the offline smb share.  On the other hand, the XP home machine fails gracefully when one the machines it has mapped drives to is powered off.

Is there any way to configure Ubuntu to keep a persistent connection to a smb share that is not always online?  I'd like to be able to power one of my computers off without having to worry about manually umounting the smb share first on Ubuntu. 

The reason I don't want to move all of the shared folders to the server is that I have a lot of data and not enough hard drive space on the server machine.

---

