---
title: "Getting Intersil ISL3886 wirless PCI card to work"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by Fraser67 on 2007-11-27
I have been struggling for days looking at the forums and trying to fix this but no joy, so can anybody please help?

I have a Fujitsu Siemens Amilo D 1845 which has an Intersil ISL3886 wireless card in it. I need to configure it so that WPA works. I am using Ubuntu 7.10.

I have followed some tips detailed in [http://ubuntuforums.org/showthread.php?t=332857](http://ubuntuforums.org/showthread.php?t=332857)

However as part of the install process for ndiswrapper when I type 

$ sudo ndiswrapper -l
 I get something like

Installed drivers:
prisma00                driver installed (alternate driver prism54)

sudo lshw -C network, also details that the ndiswrapper + prisma00 is associated with ISL3886 card as the driver but the card will not allow me to configure it with iwconfig and iwpriv.

I am sure there must be a conflict between the ndiswrapper prisma00 and prism54 driver. The problem is no matter what I do I can't  remove the prism54 driver. Blacklisting prim54 does not work, rmmod prism54 does not work.

So does anyone know how I can remove prism54 so when I install the windows driver with ndiswrapper I don't get the prism54 linked as an alternative driver? Do I need to recompile the kernel with prism54 taken out? If so how do I do this?

Thanks in advance, you will make me a happy Ubuntu.

---

### Post by Fraser67 on 2007-11-28
The problem was, having already configured one computer that used SerialMonkey rt73 drivers that used ifconfig, iwconfig and iwpriv I did not realise that these commands are not applicable when using a driver within Ndiswrapper and I needed to use commands that go with WPA-supplicant as detailed in [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) . 

It all now work and the fact that sudo ndiswrapper -l details an alternative driver does not matter.
:)

---

