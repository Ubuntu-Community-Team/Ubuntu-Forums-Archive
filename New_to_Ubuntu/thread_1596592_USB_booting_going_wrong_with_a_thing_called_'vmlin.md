---
title: "USB booting going wrong with a thing called 'vmlinuz'"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Fireblasto on 2010-10-14
Hello there :) 

I basically have a problem booting of my manually created ubuntu system - made with these instructions - 

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent). 

I try and boot of it slecting the usb in the bois menu, and from there I am greeted with this screen -

 [http://img145.imageshack.us/img145/8002/101012160648.jpg](http://img145.imageshack.us/img145/8002/101012160648.jpg) . It does nothing from there, just the live cd loading thingy screen. I can press f1 and get up the ubuntu menu, but every time I click on to 'start ubuntu 10.04 in persistent mode' it just pops up with 'vmlinuz' again.


Any idea what is causing this? Thank you,

---

### Post by C.S.Cameron on 2010-10-14
Check the MD5SUM of your iso:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you have burned the CD try the Startup Disk Creator that comes with it.

---

### Post by Fireblasto on 2010-10-14
The iso that I've got is 100% clean, and I didn't use it, I used the live CD that a friend burnt for me. Works perfectly so I'm pretty sure thats not the issue. I thinking I'm missing a file or the entire kernel bit on my usb.

Not particularly helpful though thanks for the post.

---

### Post by Ben Page on 2010-10-14
Use the Universal USB creator to create your USBuntu

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

it's easy as 1,2,3 :)

---

### Post by Fireblasto on 2010-10-14
Already tried that, doesn't want to boot of it from any computer whatsoever.

---

### Post by Ben Page on 2010-10-14
Which distro are you installing? It worked numerous times for me. Be sure to select the correct distro from the menu, check to format your drive and select the size of casper file. Your drive has to be at least 2GB for persistent installation.

Have you checked if those PCs you are trying to boot meet the minimum requirements for whatever distro you are installing? Also if they have USB boot support?

---

### Post by Fireblasto on 2010-10-14
Ubuntu 10.04.1; did all that you said; USB is 8 GB; PCs Meet all requirements and can boot of usb.

But that isn't the issue, the way that I've done it, it actually boots of the drive, I just get an error of 'vmlinuz'

PS I'm not a complete ubuntu idiot, even though I am posting the newbie section of this forum.

---

### Post by Ben Page on 2010-10-14
We all have to start somewhere :)
I'm not Ubuntu expert either, but I have done this many times, that's why I'm trying to help. I have 10.04 running off of USB pendrive at the moment. I created it via Universal USB creator, it runs from the USB drive, no installation needed, like a live CD but with the casper-rw file it can store your settings and installed apps (it is persistent). Just try it, even Ubuntu site recommends it.
Your current drive has corrupted bootloader, if you insist on your way, just redo your installation on the USB drive.

---

### Post by Calash on 2010-10-14
What method from that page did you use to make the key?


It looks like there may be an error in syslinux.cfg file, or the kernel image is not where it should be.  There are a few variations of the process on the page you linked and it seems like the location would vary depending on what version you followed.


Edit:

Assuming you followed Method 3 you have to double check your syslinux.cfg file.  Make sure the kernel line does not have the /cdrom/ path

```

kernel vmlinuz

```

That file, vmlinuz, should be located in the root of the USB key.

---

### Post by Fireblasto on 2010-10-14
I just checked the file (I did indeed use method 3) and found that there is no /cdrom /path in there.  :neutral: 

However, where would the the file vmliunz be within the file system?

---

### Post by Calash on 2010-10-14
It should be in the root directory of the first partition, at least based on the file.

I am finding some oddities in the page you linked.  I think there are errors in it that are causing your issues.  Check out this document as it appears to be the source.

[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2)

The key part that I am not finding is this line

> 
as well as files: 'casper/vmlinuz', 'casper/initrd.gz' and 'install/mt86plus'


Try copying those files on the USB key from where they are now to the root and see if that gets the key to boot.

Edit: You may be able to get away with just moving the vmlinuz from the casper directory to the root.  From what I am reading in the syslinux.cfg it should load the initrd.gz from in the casper directory where it is now.

---

### Post by Fireblasto on 2010-10-14
I did what you suggested, and it still didn't work. :/

Oh well, he's the syslinux.cfg as it appears on my system :

GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL persistent
  menu label Start Ubuntu 10.04.1 in ^persistent mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.gz quiet splash --
LABEL live
  menu label ^Start or install Ubuntu
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=/casper/initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=/casper/initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=/casper/initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY syslinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

---

### Post by Calash on 2010-10-15
Try changing the top part of the script to look like this


```

DEFAULT persistent
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=preseed/ubuntu.seed boot=casper initrd=casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL persistent
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append  file=preseed/ubuntu.seed boot=casper persistent initrd=casper/initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --

```



Your append line is not specifying the root.  That may explain why it is failing.

---

### Post by Fireblasto on 2010-10-15
Well, I had a brainwave before I turned of the pc last night and replaced all the kernel vmlinuz lines with:

kernel /casper/vmlinuz

and shockingly enough, it worked! It didn't popup with vmlinuz anymore. but here's the thing... it now pops up with casper/initrd now... great result...

---

### Post by Calash on 2010-10-15
> **Fireblasto said:**
> Well, I had a brainwave before I turned of the pc last night and replaced all the kernel vmlinuz lines with:

kernel /casper/vmlinuz

and shockingly enough, it worked! It didn't popup with vmlinuz anymore. but here's the thing... it now pops up with casper/initrd now... great result...

At least it is a result.  That seems to say that vmlinuz is not in the root of the USB.  This is fine and it "should" work as it is.  We will find out once we get all the key parts of the OS loading.

Looking at the post I linked there is a comment with a solution.  I will quote it here.

> 
Excellent tutorial - I tried so many other ways and failed.
There were 2 corrections I had to make when creating the new syslinux.cfg in step 3.3:
1. Change all occurences of initrd.gz to initrd.lz - as this is the actual name of the file
2. prefix all occurences of initrd.lz with casper/, so they should now read:
... initrd=casper/initrd.lz ....
Cheers
Jon Pilgrim


In the casper directory confirm that there is a file named initrd.lz.  If so make the listed changes to the syslinux.cfg file and try again.

---

### Post by Fireblasto on 2010-10-15
Good result again! 

'=casper/intrid.lz' didn't work but it did with '=/casper/intrid.lz'.  

However, it started to boot and now I'm getting this error from the black screen:

'(initramfs) mount: Mounting aufs on /root failed: Numerical arguemetn out of domain
aufs mount failed'

However I do have a terminal to work with.... but with no idea how.

---

