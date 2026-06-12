---
title: "Installing wireless USB dongle (GN-WBKG)"
date: 2005-09-04
forum: Networking &amp; Wireless
---

### Post by Peppone on 2005-09-04
Hi,
I have a wireless USB dongle I'd like to use in Ubuntu. It's Gigabyte's GN-WBKG.

I have plugged it in but in Network Settings there is only eth0 (my regular PCI card).

I think it should work in linux since I found a comment on /. with the heading "Truly OOTB Linux friendly adapters".
[http://hardware.slashdot.org/article.pl?sid=05/08/01/1013218&from=rss](http://hardware.slashdot.org/article.pl?sid=05/08/01/1013218&from=rss)
> I've recently purchased several of the RALink 2570 (USB) based adapters and they work fabulously. I personally bought the Gigabyte GN-WBKG and have been quite pleased. Good to see this hardware with full support from the manufacturer. For PCI cards they also have 2500 chipsets equally well supported.

What should I do to get it working?

---

### Post by kadissie on 2005-09-05
It won't work automagically.  You need to install ndiswrapper and pull the driver off the CD that came with it.  Instructions are at
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto)

Robert.

---

### Post by Peppone on 2005-09-06
I installed Ubuntu using the DVD, but a friend borrowed it. I have an older Hooray CD but when Synaptic asks for the disc it wants release i386 (20050407) and refuses to accept the CD. Can I install ndiswrapper from the internet without compiling or do I have to get my DVD back?

/ Peppone

---

### Post by Peppone on 2005-09-10
I've installed ndiswrapper but also found that there is an open source driver for the chipset (RT2500).

[http://www.ralink.com.tw/supp-1.htm](http://www.ralink.com.tw/supp-1.htm)

I have downloaded the source code for the USB driver but how do I install it? I have the .tar.gx on my desktop.

I know this is a basic question but I'm new to Linux

---

### Post by Peppone on 2005-09-10
I have tried following the instructions line by line here:
[https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo)
After running  sudo insmod rt2500.ko nothing happens. Admnistration->Networking only shows Ethernet connection eth0 and a grayed out Modem connection. No Ralink.

---

### Post by MTZeon on 2006-10-29
I have one of those and it is automatically detected in Ubuntu 6.10 ;) and its working!

---

