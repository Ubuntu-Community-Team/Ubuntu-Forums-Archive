---
title: "Hummingbird 56k Linmodem"
date: 2005-04-18
forum: Networking &amp; Wireless
---

### Post by Nimlot on 2005-04-18
I'm running Ubuntu 5.04 and need some help getting my Hummingbird 56k V.92 modem (installed on windows COM4, which is /dev/ttyS3 on Linux, right?) to work. Autodetect is not detecting it.

The modem came with Linux drivers (a .tar.gz file and .patch file), and a guide for installing them on Red Hat  9.0 Kernel 2.4.20-8. I'm not entirely sure how (and if) I would do the same thing with Ubuntu (obviously step 1 will be different). The instructions are as follows:
> 
1. Install "Development Tools" and "Kernel Development Tools" from the Red Hat CD.
2. Insert modem drivers CD-ROM
3. Enter these commands in the root terminal:
[root@localhost root]# mount /mnt/cdrom
[root@localhost root]# mcopy /mnt/cdrom/Driver/internal/Linux/slmdm-2.7.15.tar.gz
[root@localhost root]# tar zxvf slmdm-2.7.15.tar.gz
[root@localhost root]# cd slmdm-2.7.15
[root@localhost slmdm-2.7.15]# make KERNEL_INCLUDES:=/usr/src/linux-2.4.20-8/include
[root@localhost slmdm-2.7.15]# make install-amr
[root@localhost root]# rm -f /dev/ttyS1
[root@localhost root]# ln -s /dev/ttySL0 /dev/ttyS1

Can anyone explain to me how to do this or point me at a wikipage/webpage/thread that explains it?

---

### Post by az on 2005-04-18
Ubuntu uses the 2.6 kernel.  

You need the sl-modem drivers:  Download them here:

[http://ubuntuforums.org/showpost.php?p=117356&postcount=34](http://ubuntuforums.org/showpost.php?p=117356&postcount=34)

All you need to do is install them.  You do not need to compile....  Well, if you ever change kernels you will need to compile...

---

### Post by Nimlot on 2005-04-18
Installed both sl-modem packages, but still no luck. I'm getting:
> 
--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Also in /dev, modem is listed as being a broken symlink.

I also have a broadcom modem on COM3, which I don't plan on using with Ubuntu (forum searches seem to indicate it will be much harder to set up), could it be causing a problem?

---

### Post by Nimlot on 2005-04-19
Installed both sl-modem packages, but still no luck. I'm getting:
> 
--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Also in /dev, modem is listed as being a broken symlink.

I also have a broadcom modem on COM3, which I don't plan on using with Ubuntu (forum searches seem to indicate it will be much harder to set up), could it be causing a problem?

---

### Post by Nimlot on 2005-04-20
Installed both sl-modem packages, but still no luck. I'm getting:
> 
--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Also in /dev, modem is listed as being a broken symlink.

I also have a broadcom modem on COM3, which I don't plan on using with Ubuntu (forum searches seem to indicate it will be much harder to set up), could it be causing a problem?

---

### Post by Nimlot on 2005-04-21
Installed both sl-modem packages, but still no luck. I'm getting:
> 
--> WvDial: Internet dialer version 1.54.0
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory

Also in /dev, modem is listed as being a broken symlink.

I also have a broadcom modem on COM3, which I don't plan on using with Ubuntu (forum searches seem to indicate it would be much harder to set up), could it be causing a problem?

---

