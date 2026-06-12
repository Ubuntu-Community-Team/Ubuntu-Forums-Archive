---
title: "how to start the kernel"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by Yamahoj on 2009-11-04
I,m a beginner in Linux been a window man too long. Ihave downloaded Ubuntu 9.10 and burned a bootable DVD. I will evaluate Ubuntu by running it live without installation first. When I start the computer (HP 2230s laptop) with the disk in I get the boot prompt.  My problem is that I dont know what to write in the command line to get Ubunto started. Is there anybody that can help me. I´ve been browsing internet for several hours without success.

:confused:

---

### Post by Peter09 on 2009-11-04
Sounds like you have not burned the DVD correctly, make sure that you do it on the slowest speed.

Are you seeing any boot startup at all?

---

### Post by dvlchd3 on 2009-11-04
Where did you download the image from.  The Ubuntu distro is typically a CD image.

Also, when the Live CD boots, it should give you the options graphically, there should be no need to type anything in.

If you downloaded a custom ISO image, you may try simply hitting [enter].

The official download site is:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by NickJones on 2009-11-04
Make sure you have properly burned the CD. Standard computers boot normaly by default from the CD drive, and if they don't find anything to boot from there, they boot from the HDD, so it sounds like the CD is corrupt or improperly burned. Try re-burning or if that fails, re-download the disk image, and make sure you get the official one. And if you do know how to torrent, please don't download from the site, download it from the torrent available from the site.
Nick

---

### Post by Yamahoj on 2009-11-04
Yes i have downloded Ububtu from Ubuntu.com. I get a prompt boot: with a blinking underscore sign. If I write anything there it responds with the following "could not find kernel image:

---

### Post by Peter09 on 2009-11-04
Try burning again, this time, with any settings on the 'slow' value.
Are you sure you downloaded the correct image, what image did you download?

---

### Post by Yamahoj on 2009-11-04
Ive got many folders and files on the disk.

This information is in the readme file in the disk folder.


#define DISKNAME  Ubuntu 9.10 "Karmic Koala" - Release i386
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1

---

### Post by Peter09 on 2009-11-04
mmm - you need to try reburning, I think you have a corrupt DVD

---

### Post by phillw on 2009-11-04
> **Yamahoj said:**
> Ive got many folders and files on the disk.

This information is in the readme file in the disk folder.


#define DISKNAME  Ubuntu 9.10 "Karmic Koala" - Release i386
#define TYPE  binary
#define TYPEbinary  1
#define ARCH  i386
#define ARCHi386  1
#define DISKNUM  1
#define DISKNUM1  1
#define TOTALNUM  0
#define TOTALNUM0  1

Check that your dowloaded file is okay -- [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
As noted, burn at 4X speed
Check the CD, the same way as you checked the file.

Also, do ensure you grabbed the desktop version and not the server version, and that you got either 32bit or 64 bit - dependant on what your computer is.

Phill.

---

### Post by Yamahoj on 2009-11-10
Thanks for your help I did burn my DVD with the 4x speed and that worked fine. After that I made a bootable USB stick successfully by using the utility under <system> <Administration> "USB startup disk creator" tool and that pretty easy.
 My difficulty now is to get the WLAN working. I have an Airport Extreme router that works fine when I run Vista on my laptop. Can somebody help me to find a guide how to perform the setup?

---

### Post by SeanHodges on 2009-11-10
In my experience, you will do better to start a new thread for this problem. Otherwise everyone will assume you are still asking about "starting kernels" rather than setting up a Wireless network.

---

### Post by 3rdalbum on 2009-11-10
The wireless router isn't the important bit. The important bit is your wireless card.

First I'd suggest plugging your computer into the router using an Ethernet cable (this will automatically get you a wired internet connection) and hit the Reload button in System > Administration > Synaptic Package Manager. After that's finished, close Synaptic and go to System > Administration > Hardware Drivers. Hopefully you should have a driver listed that can be downloaded and installed for you.

If this doesn't work, then please go to Applications > Accessories > Terminal and in the window that appears, type the following:

```
lspci
lsusb
```

(that's "ell-ess-pea-sea-eyhe" and "ell-ess-you-ess-bee").

Copy and paste the output into a new post on here and we might be able to help you.

---

