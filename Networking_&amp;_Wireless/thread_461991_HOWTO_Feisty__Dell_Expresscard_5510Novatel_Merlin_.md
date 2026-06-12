---
title: "HOWTO Feisty:  Dell Expresscard 5510/Novatel Merlin XU870 in Airprime!"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by bimmerd00d on 2007-06-02
This card is also a Novatel Merlin XU870.  Here's how i set it up on my Dell Latitude D820, with some help from a fellow poster on here as well :)  Keep in mind this is for the Expresscard version, i believe the internal mini-pciE is the 5500 model which already works in the stock airprime.ko driver, so you could skip the kernel module stuff i you have this one.  You will need to repeat this again after a kernel upgrade.  Maybe they'll add it to the stock airprime driver soon :)

Install the minimum build environment, Linux sources, and Linux headers for your currently-running kernel:
```
sudo apt-get install build-essential linux-headers'uname-r linux-source-'uname-r
```


Next, lets double check that our dell card has the same hardware/product ID that mine does,  (it should)  make a note of it, or just leave the terminal open.  You're looking for something like


```
 lsusb


Bus 005 Device 002: ID **413c:8118** Dell Computer Corp. 
 
```

Go into /usr/src/ and uncompress the kernel source code:
```
cd /usr/src
sudo tar xjvf linux-source-2.6.17.tar.bz2 
```

Enter the directory containing the airprime driver:
```
cd linux-source-2.6.17/drivers/usb/serial
```

Edit your airprime.c
```
sudo gedit airprime.c
```

You'll then see the contents of this file and i've highlighted what you need to add in bold.
```
/*
 * AirPrime CDMA Wireless Serial USB driver
 *
 * Copyright (C) 2005-2006 Greg Kroah-Hartman <gregkh@suse.de>
 *
 *	This program is free software; you can redistribute it and/or
 *	modify it under the terms of the GNU General Public License version
 *	2 as published by the Free Software Foundation.
 */

#include <linux/kernel.h>
#include <linux/init.h>
#include <linux/tty.h>
#include <linux/tty_flip.h>
#include <linux/module.h>
#include <linux/usb.h>
#include <linux/usb/serial.h>

static struct usb_device_id id_table [] = {
	{ USB_DEVICE(0x0c88, 0x17da) }, /* Kyocera Wireless KPC650/Passport */
	{ USB_DEVICE(0x1410, 0x1110) }, /* Novatel Wireless Merlin CDMA */
	{ USB_DEVICE(0x1410, 0x1130) }, /* Novatel Wireless S720 CDMA/EV-DO */
	{ USB_DEVICE(0x1410, 0x2110) }, /* Novatel Wireless U720 CDMA/EV-DO */
	{ USB_DEVICE(0x1410, 0x1430) },	/* Novatel Merlin XU870 HSDPA/3G */
	{ USB_DEVICE(0x1410, 0x1100) }, /* ExpressCard34 Qualcomm 3G CDMA */
	{ USB_DEVICE(0x413c, 0x8115) }, /* Dell Wireless HSDPA 5500 */
	**[SIZE="3"]{ USB_DEVICE(0x413c, 0x8118) }, /* Dell Wireless HSDPA 5510 */[/SIZE]**
	{ },
};
```

To compile only the airprime dirver (this actually compiles all drivers in the directory):
```
sudo make -C /lib/modules/`uname -r`/build M=`pwd`(where 'pwd' is /usr/src/linux-source-2.6.20/........, 

this confused me at first, but i'm noobtastic)
```

Then you want to copy the created airprime.ko driver to the correct location and run depmod
```
sudo cp airprime.ko /lib/modules/2.6.20-.........  /kernel/drivers/usb/serial/airprime.ko

sudo depmod -a
```

Now i'm not sure if this is required, but i did it anyway and it still works 100%.
```
sudo gedit /etc/modules

add airprime to the list of modules at startup
```

Head over to Novatel's site and download their scripts and follow their instructions. 
[http://www.novatelwireless.com/support/merlin-xu870-linux.html](http://www.novatelwireless.com/support/merlin-xu870-linux.html)

Now you should be able to connect to Cingular at the fast speeds with airprime. Usbserial worked just fine, but i couldn't get over 256kb/s, now i'm getting up to 1.5mbps and i'm happy.  Removal and reinserting works fine, i haven't experienced any issues yet.  I am about to writeup how to get network manager to handle the connections, and then i'll add another one for how to make Conky display the current connection info :D

Thanks go to jdericho for helping me set this up initially

Make NetworkManager handle the connection: [http://ubuntuforums.org/showthread.php?p=2767425#post2767425](http://ubuntuforums.org/showthread.php?p=2767425#post2767425)
Setup Conky to display ppp0 stats: [http://ubuntuforums.org/showthread.php?t=461997](http://ubuntuforums.org/showthread.php?t=461997)

Here is my list of sources if you want to check them out:
[http://www.marotori.com/blog/?cat=12](http://www.marotori.com/blog/?cat=12)
[http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html](http://samat.org/weblog/20070127-high-speed-cellular-wireless-modems-in-ubuntu-linux-6-10.html)

---

### Post by mfrauenstein on 2007-07-20
Thanx for the help. I have a Merlin XU870 card in a Ferrari 4000 now working. Followed the instructions on the Novatel web site, made some changes for the Vodafone network in New Zealand and it works. By the way I am running Feisty 7.04

---

### Post by skulls on 2007-07-23
Hi,

I've read tens of posts regarding this card, and I *can't* get it to work on Feisty!

It works fine on windows so a hardware problem is out of question. I've followed the steps described at [www.novatelwireless.com/support/merlin-xu870-linux.html](www.novatelwireless.com/support/merlin-xu870-linux.html) with no success :(

What happens is that when I connect the card and start looking at tail –f /var/log/messages, the card shows up and a few seconds later it says that 'airprime converter now disconnected from ttyUSB0' (and ttyUSB1 and so on all the way up to ttyUSB11). So I don't get a chance to run the following commands. 

Any ideas???:confused::confused::(

Your help will be greatly appreciated!

P.s: I'm running Feisty 7.04 on an ASUS U1F laptop, no problems so far except for this.

---

### Post by skulls on 2007-08-22
After weeks of no answers and lots of research, I finally came across a nifty little program called umtsmon, which has solved all my problems! It can auto-detect the card and connect all by itself. Definitely recommended if you don't want to mess around.

---

### Post by emja on 2008-05-28
Your sig indicates you're now running Hardy. I presume you've got your XU870 working on your new Hardy installation?

Can you please update your HOWTO with any info relating to Hardy & the XU870?

cheers!

---

### Post by motin on 2008-06-25
> **skulls said:**
> After weeks of no answers and lots of research, I finally came across a nifty little program called umtsmon, which has solved all my problems! It can auto-detect the card and connect all by itself. Definitely recommended if you don't want to mess around.

> **emja said:**
> Your sig indicates you're now running Hardy. I presume you've got your XU870 working on your new Hardy installation?

Can you please update your HOWTO with any info relating to Hardy & the XU870?

cheers!

Thanks! umtsmon did not prevent having to modprobe usbserial with vendor and product codes, but once done, umtsmon worked flawlessly! Thanks for the tip!

---

### Post by mptpro on 2008-07-02
Can someone please give me some guidance on how to install umtsmon?

I can't seem to find the .deb package?

(I do miss the days of .exe installs on windows!)

:confused:


In addition, the support site at novatel is down.  And I do not have the linux drivers.  They were not on the cd.

any help? Thanks

---

### Post by motin on 2008-07-24
> **emja said:**
> Your sig indicates you're now running Hardy. I presume you've got your XU870 working on your new Hardy installation?

Can you please update your HOWTO with any info relating to Hardy & the XU870?

cheers!

I just compiled the modified airprime module on Hardy:

Initial apt-get instruction to one that works:
```
sudo apt-get install build-essential linux-headers-`uname -r` linux-source
```

Distro-generic versions of the unzip and enter the correct location in kernel sources:
```
sudo -s
cd /usr/src
sudo tar xjvf linux-source-2.6.*.tar.bz2
cd linux-source-2.6.*/drivers/usb/serial
```

My current airprime.c now looks like this:
```
static struct usb_device_id id_table [] = {
	{ USB_DEVICE(0x0c88, 0x17da) }, /* Kyocera Wireless KPC650/Passport */
	{ USB_DEVICE(0x413c, 0x8115) }, /* Dell Wireless HSDPA 5500 */
	{ USB_DEVICE(0x0930, 0x1303) }, /* Toshiba (Novatel Wireless) HSDPA for M400 */
	{ USB_DEVICE(0x106c, 0x3701) }, /* Audiovox PC5740 */
	{ USB_DEVICE(0x106c, 0x3702) }, /* Sprint Pantech PX-500 DGE */
	{ USB_DEVICE(0x1410, 0x4100) }, /* Novatel Wireless U727 */
	{ USB_DEVICE(0x12d1, 0x1003) }, /* Huawei E220 */
	{ USB_DEVICE(0x05c6, 0x6000) }, /* Momo design */
	{ USB_DEVICE(0xf3d0, 0x0112) }, /* AirPrime 5220 */
[B]	{ USB_DEVICE(0x413c, 0x8115) }, /* Dell Wireless HSDPA 5500 */
	{ USB_DEVICE(0x413c, 0x8118) }, /* Dell Wireless HSDPA 5510 */
	{ USB_DEVICE(0x413c, 0x8138) }, /* Dell Wireless HSDPA 5520 aka Expedite EU870D MiniCard (Shipped with Dell XPS Laptops) */[/B]
	{ },
};

```

Compiling instructions are the same as in the guide.

Distro-generic for copying the compiled version to the right directory (and performing a backup of the original):
```

sudo cp /lib/modules/`uname -r`/kernel/drivers/usb/serial/airprime.ko ~/airprime.ko.org.bak
sudo cp airprime.ko /lib/modules/`uname -r`/kernel/drivers/usb/serial/airprime.ko
sudo depmod -a

```

However I cannot continue with:
> Head over to Novatel's site and download their scripts and follow their instructions.
[http://www.novatelwireless.com/support/merlin-xu870-linux.html](http://www.novatelwireless.com/support/merlin-xu870-linux.html)
...since that URL is broken...

What was provided there? What were the instructions? Are they available at some other place?

> **motin said:**
> Thanks! umtsmon did not prevent having to modprobe usbserial with vendor and product codes, but once done, umtsmon worked flawlessly! Thanks for the tip!

I am correcting myself here: Yes, UMTSMon is great, but this tutorial is not merely about getting connected to the internet. No it's about achieving higher speeds than around 60 kb/s! Currently that's what I have gotten so far when using usbserial - and various sources (including this one...) advices use of airprime in order to utilize HSDPA speeds...

So - You will want UMTSMon *but that won't replace the OP's Howto in this thread*!

> **mptpro said:**
> Can someone please give me some guidance on how to install umtsmon?

I can't seem to find the .deb package?

(I do miss the days of .exe installs on windows!)

:confused:

In addition, the support site at novatel is down.  And I do not have the linux drivers.  They were not on the cd.

any help? Thanks

Well, since you are asking for it: [**HOWTO: Install UMTSMon (GUI for 3g/HSDPA connections)**]("http://ubuntuforums.org/showthread.php?p=5449081#post5449081")
It's a quick write-up - hope it works!

---

### Post by motin on 2008-07-24
Found a Novatel Linux guide: [http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176:linuxsetupumts&catid=43:linux-installation-instructions&Itemid=331](http://www.novatelwireless.com/index.php?option=com_content&view=article&id=176:linuxsetupumts&catid=43:linux-installation-instructions&Itemid=331)

Although it is all about configuring the modem _after_ usbserial etc has been loaded - and terrible instructions as well! Use UMTSMon instead of following these instructions...

---

### Post by motin on 2008-07-24
Nah... with only the airprime module loaded, I can still connect using UMTSMon but my connection still doesn't reach speeds above ~60 kb/s!

Seems like the issue instead is that I'm for some reason not using anything but UMTS (never HSDPA... even UMTSMon only displays HSDPA after "Network: ").

For anyone interested in helping me with this UMTS-issue: [The internal 3g modem never uses turbo-3g... (HSDPA) - only UMTS]("http://ubuntuforums.org/showthread.php?t=866387")

Thanks!

---

