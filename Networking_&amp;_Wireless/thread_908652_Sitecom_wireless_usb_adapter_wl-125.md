---
title: "Sitecom wireless usb adapter wl-125"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by newtubunix on 2008-09-02
Hi,
I wanted to get my wireless usb adapter working with ubuntu, but i was experiencing some problems and before i can ask my question, i have to explain some things that happened.
I have a Sitecom WL-125 Wireless USB 2.0 adapter 100g+&#8207; and i tried to find a native driver for linux, but have not been able to find that so far. (lsusb gives me this ID for the usb: 
Bus 002 Device 003: ID 3574:907d)
Then i found a package(compat-wireless from [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download) with the latest native drivers all together. I thought that if it had a native driver, this would be working, because you can load all the drivers together. Here i must mention that i tried it on a laptop which has a built-in Broadcom wireless adapter, which uses the b43 driver also included in the package. The Broadcom adapter could work without the package because i already installed b43 alone.
After i installed the package i unloaded all the previous drivers and then loaded all the drivers that were included in the compat-wireless package. The Broadcom adapter still worked and i thought that the usb was not recognized, but as i found out , it was working somewhat. In the device list it was not recognized because the iwconfig option gives me the l0, eth0, wmaster0 and wlan0, which were already there before i plugged the usb device in. However i had far better connectivity with my network and network manager detected far more networks of my neighbours, wich i never detected with only my Broadcom adapter. I am quite sure that it isn't only the Broadcom adapter that is working, because when i unplug the usb device again, about half of my neighbours networks disappear immediatly after that.
So to summarize:
If i plug the usb device in and turn on the built-in adapter, only the built-in is recognized, but i can detect networks that would only be possible if my usb device was working.
If I unplug the usb device and let the built-in adapter on i could detect far less networks and connection is not as good as before.
If the usb device is plugged in , but my built-in adapter is turned off i have no connectivity at all and no networks at all are detected.
And now finally my question:
I still haven't find which driver should be used for that chipset of my usb. Any help with that is welcome(probably it is one listed in the compat-wireless package)
And if i have that driver, i actually want it to use for another computer which hasn't a built-in adapter, so how could that be done?
Many thanks for your help

PS: I don't want to use ndiswrapper or something alike.

---

