---
title: "No wifi after fresh ubuntu 11.04 install, presario C500"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Woody Framer on 2011-04-30
Is anybody else having issues with wifi drivers after installing ubuntu 11.04??

I've done a fresh install and have the additional driver activated for broadcom but can't seem to get the wifi to work- no blue light on wifi connect button.

I'm using a Compaq C500

This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware.

many thanks

---

### Post by khaj_vah on 2011-04-30
Well, mate update your ubuntu.i couldn't have my wifi adapter to work also on 10.10 but after update all worked just try.

---

### Post by Patrick Janssen on 2011-04-30
Same computer, same story, same problem here. Which is really weird 'cause I've been working with Ubuntu fot three weeks now and everything just worked great. Tried the old fashioned windows way: remove the broadcast driver an reinstall. no budge. I just found a usb d-link wifi, with wich I am able to get online and ask for help.

I wonder what changed and makes ubuntu 11.04 unable to use this wifi.

---

### Post by Adam590 on 2011-04-30
I also have the same computer and problem. The Broadcom STA driver seems to be in place, but the network/card is showing as UNCLAIMED. Worked fine before the switch to 11.04.

> **khaj_vah said:**
> Well, mate update your ubuntu.i couldn't have my wifi adapter to work also on 10.10 but after update all worked just try.

Was this also with a Presario C500? Or a different machine that uses the same driver? I'd love to hear that someone got one working.

---

### Post by rduverge on 2011-04-30
I had the same problem, but i was able to fix it removing the drivers and installing another version of the broadcom drivers.

You have to download this drivers [I][http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) , after downloaded remove the old drivers using terminal with this code:
[/I][I]sudo apt-get remove bcmwl-kernel-source

After that, double click the new drivers to install them, reboot and problem will be fixed!.


[/I]

---

### Post by Adam590 on 2011-04-30
> **rduverge said:**
> I had the same problem, but i was able to fix it removing the drivers and installing another version of the broadcom drivers.

You have to download this drivers [I][http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) , after downloaded remove the old drivers using terminal with this code:
[/I][I]sudo apt-get remove bcmwl-kernel-source

After that, double click the new drivers to install them, reboot and problem will be fixed!.

[/I]

Wow, awesome fix! Thanks a million! I did what you said, then rebooted, and now everything works perfectly - even the little light on the button!

---

### Post by Patrick Janssen on 2011-05-01
> **rduverge said:**
> I had the same problem, but i was able to fix it removing the drivers and installing another version of the broadcom drivers.

You have to download this drivers [I][http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) , after downloaded remove the old drivers using terminal with this code:
[/I][I]sudo apt-get remove bcmwl-kernel-source

After that, double click the new drivers to install them, reboot and problem will be fixed!.


[/I]
DearRduvege, thanx a million, it worked like a charme: Problem solved. I didn't exactly do like you said (I'm a bit reluctant about using terminal etc)
so for the rookies among us:
download as mentioned above, paste the file onto your desktop
start ubuntu software centre, search for "broadcom" uninstall anything from broadcom, which is already installed.
When that's done, double click the file you copied to your desktop.
Wait for ubuntu to finish the job and restart your computer.

---

### Post by Skankyfish on 2011-05-02
We just tried this (on partner's Dell Inspiron 1501, which was working fine before update to 11.04), but with no luck.  Network connections lists the wifi connection and when it was last used, but simply won't connect.  Does anyone have any other ideas?  We are total linux noobs, so an idiots guide would be much appreciated.

---

### Post by Mizzhell on 2011-05-03
> **rduverge said:**
> I had the same problem, but i was able to fix it removing the drivers and installing another version of the broadcom drivers.

You have to download this drivers [I][http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) , after downloaded remove the old drivers using terminal with this code:
[/I][I]sudo apt-get remove bcmwl-kernel-source

After that, double click the new drivers to install them, reboot and problem will be fixed!.


[/I]

Thanks! Did this on my Dell XPS 1330 and it worked.

---

### Post by champost on 2011-05-04
Few thoughts on **rduverge**'s soultion. 

Just realised that it was only for 34 bit processors, so i tweaked the url by changing "i386.deb" to "amd64.deb" for the 64 bit version (or download [here]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")). That worked for me after having uninstalled the "5.100.82.38+bdcom-0ubuntu3" update of the STA driver (i.e. the default one in Ubuntu 11.04). Though switching over from wireless to ethernet is buggy and Ubuntu simply hangs with the "5.60.48.36+bdcom-0ubuntu5" version that **rduverge** proposes. 

I use a Dell Precision M4500.


> **rduverge said:**
> I had the same problem, but i was able to fix it removing the drivers and installing another version of the broadcom drivers.

You have to download this drivers [I][http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) , after downloaded remove the old drivers using terminal with this code:
[/I][I]sudo apt-get remove bcmwl-kernel-source

After that, double click the new drivers to install them, reboot and problem will be fixed!.


[/I]

---

### Post by Adam590 on 2011-05-11
[Others may already know this, but I wanted to have it here in the thread for me to reference later.]

Don't forget, to preserve the older working driver, once you have it in place go to Synaptic and highlight the package (name is bcmwl-kernel-source), then go to Package > Lock Version in the menu bar.

---

### Post by hdredor on 2011-07-31
Worked for me - Compag Presario C500.  Wish I had found it a few hours ago...  lol. 

Thanks!

Thanks for reminding me to lock it as well Adam590.

---

### Post by glennric on 2011-08-01
> **champost said:**
> Few thoughts on **rduverge**'s soultion. 

Just realised that it was only for 34 bit processors, so i tweaked the url by changing "i386.deb" to "amd64.deb" for the 64 bit version (or download [here]("http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb")). That worked for me after having uninstalled the "5.100.82.38+bdcom-0ubuntu3" update of the STA driver (i.e. the default one in Ubuntu 11.04). Though switching over from wireless to ethernet is buggy and Ubuntu simply hangs with the "5.60.48.36+bdcom-0ubuntu5" version that **rduverge** proposes. 

I use a Dell Precision M4500.

I want to get one of these 34 bit processors.  Those have to be worth a lot of money.  At least as a novelty item.

---

### Post by Ken.B on 2011-10-11
> **rduverge said:**
> I had the same problem, but i was able to fix it removing the drivers and installing another version of the broadcom drivers.

You have to download this drivers [I][http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb) , after downloaded remove the old drivers using terminal with this code:
[/I][I]sudo apt-get remove bcmwl-kernel-source

After that, double click the new drivers to install them, reboot and problem will be fixed!.


[/I]

Hi,

Thank you for your output. 

This is the first time I'm using Ubuntu. I'm using HP MINI 210-1000 with BCM4312.

I've successfully install the new driver. I've tick the "enable wireless" but it says that "wireless networks wireless is disabled".

Did I do anything wrong?

---

