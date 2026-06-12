---
title: "Usb hard drive install - No internet"
date: 2008-09-12
forum: Networking &amp; Wireless
---

### Post by jamesdee258 on 2008-09-12
I am a newbie.  

I have recently installed ubuntu 8.04 onto a usb hard drive.  This boots effectively from the usb drive. The Netgear modem router seems to recognise both wire connection or plug in 3 Com wireless link. Desktop indicates a good wireless link.

However there is no internet connection.  Also, once booted again from Windows Vista, the internet connection has been lost.  The only way to correct matters is to power down the Netgear modem and reboot the machine.

I have an old machine set up with ubuntu 8.04 and this links up without problems to this modem using 3 Com usb connection.

Is this a port problem?

Many Thanks

---

### Post by superprash2003 on 2008-09-12
in your terminal try pinging your router, ensure that you are getting an ip address by typing ifconfig in your terminal.

---

### Post by jamesdee258 on 2008-09-22
Thanks for reply.

I still cannot connect to internet using usb HDD.  However I have managed to connect successfully on usb flashdrive.

On running ifconfig I effectively get the same information (apart from RX and TX packets etc.).  The 1M flash drive lists eth0 and l0.  The HDD lists eth2 and l0.

I had some problems with the flashdrive and did not connect to internet at first.  The problem has cleared with the flashdrive but I am unable to replicate with the HDD.

I think it must be a port problem.  I have tried connection with fixed IP address to no effect.

Any ideas?

Many Thanks

jamesdee258

---

