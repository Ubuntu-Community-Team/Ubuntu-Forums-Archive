---
title: "Trouble with samba and setting up a home network"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by Vanion on 2008-11-23
Hi there, I'm rather new to linux. I recently decided that i'd like to use my slightly dated pc as a home file server for myself and my roommates to share media on.

Following the advice of various guides I set up the pc with two hard drives: a 40GB drive to hold Ubuntu, and a larger drive (NTFS) to share.

I followed this guide: [http://ubuntu-8-1.blogspot.com/2008/07/how-to-share-domain-in-ubuntu-with.html](http://ubuntu-8-1.blogspot.com/2008/07/how-to-share-domain-in-ubuntu-with.html)

and got as far as sharing the folders.  here's where I screwed up.  I tried to change the mount point (knowing little about doing so) of my shared HD but after a reboot the drive is now inaccessible.  When i try to access it, it says:

> 
Cannot mount volume.
The volume 'SHARE' uses the *NTFS* file system which is not supported by your system.


any help would be greatly appreciated

---

### Post by Iowan on 2008-11-24
[Here]("http://ubuntuforums.org/showthread.php?t=288534") is a good How-To for mounting CIFS shares, but may not be quite what you're looking for. You might post your **fstab**, but it's likely that the drive should be mounted as CIFS instead of NTFS.

---

### Post by superprash2003 on 2008-11-24
also do you see the "SHARE" shared folder when you access smb;//127.0.0.1 ??

---

