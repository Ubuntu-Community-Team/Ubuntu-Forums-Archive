---
title: "Comstar 500 RJ45 External Hard Drive - NAS problem"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by dbqp on 2008-04-01
I recently purchased a Comstar 500 External Drive which has both the USB and RJ45 interface. I am using the RJ45 interface for Network Attached Storage.

The software that came with the drive is, of course, Windows based. Installing the software seems to be the only way to access this drive.

Would anyone be able to provide guidance on getting this drive to be recognized in Ubuntu?

It is formatted a vfat32 and I have looked at my device connections for my router, but the drive is not listed to obtain an IP address.


I can access it from the couple of Windows PC's running on the same network.

---

### Post by dstew on 2008-04-01
My guess is that the NAS will be using a Windows-style network, which can be accessed by Ubuntu using Samba if you can configure it. Try the Samba command [nmblookup]("http://www.hmug.org/man/1/nmblookup.phpnet") to see if you can get the right netbios name. This command has worked for some```
nmblookup -T "*"
```See [this thread]("http://ubuntuforums.org/showthread.php?t=735024&highlight=NAS").

---

### Post by dbqp on 2008-04-01
Thanks for the reply, but it appears this NDAS drive has a whack of problems using mixed environments.

See the following URL - post number 8

[Future Shop Forum]("http://www.futureshopforums.ca/futureshop/board/message?board.id=add-ons&thread.id=361")

Maybe I'll just go back to the USB interface and connect it to my Ubuntu Server. I was just all excited about having NAS storage attached to my network...

Feel free to post your two cents if you have something to add because I would still like to access this through the RJ45 connection.

---

### Post by dbqp on 2008-04-01
Well, great news! NDAS has provided a Linux set of drivers for these types of products!

I came across the XIMETA (They developed NDAS Technology).

You can find Ubuntu and other linux distros supported here:

[http://www.ximeta.com/web/support/download/linux/index.php](http://www.ximeta.com/web/support/download/linux/index.php)

---

### Post by dstew on 2008-04-01
Yes, it seems the NDAS protocol is proprietary, so you will definitely need Linux drivers. Let us know if you can get it to work as a network drive. Good luck.

---

### Post by dbqp on 2008-04-01
> Yes, it seems the NDAS protocol is proprietary, so you will definitely need Linux drivers. Let us know if you can get it to work as a network drive. Good luck.

Thanks. I cannot wait to get home to try this out! I'll definitely update this thread with my results.

---

### Post by dstew on 2008-04-01
Looking at the Ximeta site, it seems [this page]("http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB") is the place to go. You build a Debian package from source.

---

### Post by dbqp on 2008-04-09
> Looking at the Ximeta site, it seems this page is the place to go. You build a Debian package from source.

Well, I finally got around to building the DEB file and tried it out. The installer seemed to work, but I could never "get" to it to find it on the network for mounting.

I'll post back with more.

---

### Post by dbqp on 2008-04-11
Here is what I get after installing the deb file created:

```
david@ubT30:~$ sudo dpkg -i ndasadmin_1.1-13_i386.deb
[sudo] password for david:
dpkg: error processing ndasadmin_1.1-13_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ndasadmin_1.1-13_i386.deb
david@ubT30:~$ cd Desktop
david@ubT30:~/Desktop$ sudo dpkg -i ndasadmin_1.1-13_i386.deb
(Reading database ... 107010 files and directories currently installed.)
Preparing to replace ndasadmin 1.1-13 (using ndasadmin_1.1-13_i386.deb) ...
Stopping NDAS: synced umounted synced stopped modules removed
Unpacking replacement ndasadmin ...
Setting up ndasadmin (1.1-13) ...
Starting NDAS: modules inserted. NDAS driver is initialized.
 started

```

After this, I don't know how to locate the drive...

---

