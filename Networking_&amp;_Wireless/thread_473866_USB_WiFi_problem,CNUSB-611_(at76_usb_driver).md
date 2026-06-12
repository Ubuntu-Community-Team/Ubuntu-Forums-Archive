---
title: "USB WiFi problem,CNUSB-611 (at76_usb driver)"
date: 2007-06-14
forum: Networking &amp; Wireless
---

### Post by frenchie091 on 2007-06-14
Hi,
my CNet (CNUSB-611) USB wifi interface worked straight away with Ubuntu (Edgy, then Feisty). But I've recently been having problems. On boot, the card doesn't seem to be recognised, even though the at76_usb driver module is loaded. When I do  restart networking, it reports that the device doesn't exist. If I remove the card and plug it in, it generally starts up ok then (I use the Gnome netowrk manager applet to check what's happening), though sometimes I have to restart networking.

I'm stumped as to what might be causing this. Might it be due to the order in which the modules are loaded, i.e. maybe the driver is being loaded before USB support has been set up properly? That's a guess, and I don't know how to check the order of module loading.

Any help much appreciated, I'm in the process of banishing Windows from my life (hopefully) forever, and would love to fix this little snag.

Thanks,
John.

---

