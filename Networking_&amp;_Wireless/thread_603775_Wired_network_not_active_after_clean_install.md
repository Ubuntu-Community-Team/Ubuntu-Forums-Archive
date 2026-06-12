---
title: "Wired network not active after clean install"
date: 2007-11-05
forum: Networking &amp; Wireless
---

### Post by sipickles on 2007-11-05
Hi,

After installing Gutsy in a dual boot setup, I can't get an internet connection. I did have a ping to the gateway at first, but no internet. So I disabled IPv6, which has been successful on my other PC, but this didn't help.

 In fact, several reboots later, I've finally noticed my Hub's LAN light is not lit for the port I've plugged Gutsy into. I know the cable and PCI card are good since it all works with ease in XP.

My Hardware list shows a RTL-8139/8139C/8139C+ Network card. So why is it apparently disabled?

I've tried ifup/ifdown... can anyone help a ubuntu network noob?

Thanks a million!

Si

---------------------------

if I do:

dmesg | grep eth0

I get multiple cycles saying something along the lines of:

eth0: link up, 100Mbps, full-duplex....
NETDEV WATCHDOG: eth0: Transit timeout, status 0d 0000 c87f media 10

This repeats about 8 times during the boot log.

Cananyone demystify?

---

