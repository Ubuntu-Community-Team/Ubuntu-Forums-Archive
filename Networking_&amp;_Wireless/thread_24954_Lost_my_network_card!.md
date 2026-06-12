---
title: "Lost my network card?!"
date: 2005-04-08
forum: Networking &amp; Wireless
---

### Post by ravid on 2005-04-08
Hi, 

I installed Hoary about two weeks ago, and have been loving it.  I've managed to get a bunch of servers setup, and have been flying along.  However last night my network card disappeared randomly!  I did just finish doing a apt-get upgrade (a big one, hadn't done it in about three days).  

At first I just lost my internet connection and still had eth0, after a reboot eth0 is gone.  I noticed before my reboot, that my card had only an IPv6 address (where before it had a regular IPv4 address).  Ubuntu is still seing my card with lspci:

0000:00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

but ifconfig -a only reveals two devices (loopback (lo) and something called sit0... donno what that is)

I don't really know where to go from here... any help is greatly appreciated.  Thanks!

RaViD

P.S. I've already check the cables/router/DSL modem all work perfectly

---

### Post by ravid on 2005-04-09
Just an update.  I seem to have fixed the problem. I booted into an older copy of Knoppix 3.3 to test the network card, and it work perfectly.  When I came back to ubuntu the card was magically working again.  

My guess is that the card went into a sleep mode of some sort.  I remember having this problem with this card going into a Powersave mode in earlier versions of XP.  Does anyone know if theres a place where I can specify specific options for my network card (to prevent this from happening again).  

If there isn't any real way to fix this, I may just have to "splurge" and spend 10 bucks on a new card  :)  

Cheers, 
RaViD

---

### Post by jak on 2005-04-10
I've just had the same problem.
I have sit0 and lo in ifconfig, lspci shows "0000:00:0d.0 Ethernet Controller: MYSON Technology Inc SURECOM EP-320X-S 100/10M Ethernet PCI Adapter" though. Worked after install, shutdown, boot next day and gone.

RaViD: you mentioned setting up servers? This was also a server install.

Edit: I undone the only change I thought mattered. I chmod /etc/init.d/hotplug +x again, and it worked. I chmod -x /etc/init.d/hotplug as I thought it was just for USB and this old system has no usb capabilities. Read in /etc/network/interfaces that hotplug does eth0 too, so made it executable, rebooted and its back. 
Seems this is unrelated to RaViD's post.

---

