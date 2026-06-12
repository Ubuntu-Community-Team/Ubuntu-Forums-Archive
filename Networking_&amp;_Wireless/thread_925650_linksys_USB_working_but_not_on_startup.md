---
title: "linksys USB working but not on startup"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by Cyril_Grey on 2008-09-20
Prism 2 chipset in this piece of hardware. I am using it right now so things are working but it does not start up when boot up. It will be listed in roaming mode in network manager.

I can pull the USB out and put it back in and it will pick it up and I can use it. Not sure why its not starting up at boot tho. Ndiswrapper seems to be functioning fine so its something on startup.

Anyway on to some code:

So Ndiswrapper output:
lswlusb : driver installed
	device (066B:2213) present (alternate driver: prism2_usb)

check Dmesg

[   41.233139] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   41.371695] usbcore: registered new interface driver ndiswrapper
[   41.379422] udev: renamed network interface wlan0 to wlan1
[   80.567163] wlan1: no IPv6 routers present
[  133.642119] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  134.116109] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  144.212753] wlan0: no IPv6 routers present

I googled that udev switch and didnt find a whole lot I could use. I think thats the issue but any advice on correcting it would be appreciated.

After I mess around with it I can get the net up as I said. 

Ifconfig returns the stick working under wlan0.


I think maybe this time I can drop windows for good. The new ubuntu is pretty stable for me. I can even play wow on it. Any help is appreciated. I am pretty noobish at linux so  sorry if I left something obvious out.

---

### Post by h12 on 2008-09-21
Have you tired > modprobe ndiswrapper to detect it, rather than unplugging it and plugging it back in? If that works, then you could add ndiswrapper to /etc/modules, and it should work at startup.

---

