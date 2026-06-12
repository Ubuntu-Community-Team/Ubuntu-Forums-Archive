---
title: "[SOLVED] My ethernet woes"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by Sarmacid on 2008-12-18
Here's my problem, any suggestions would be greatly appreciated.

I have an Ubuntu 8.04 server box, it has an ethernet card and no expansion slots. I need to be able to connect it to a wired network. What I've tried so far have been a couple of USB-RJ45 adapters, one that a friend lent me works great, but I have to give it back to him, the other didn't work, although dmesg showed that it was plugged and the drivers where loaded, the output of ifconfig -a showed it as usb0 and the MAC was ff:ff:ff:ff:ff:ff with no ip. I tried assigning it a different ip an later a different MAC but kept getting errors. This later adapter was the only one I found around asking in several stores, but since it doesn't work, I'm planning on returning it.

So is there any other way I could get this pc into the network? I already tried compiling the drivers on the card that didn't work and failed miserably, but if it comes down to it, I would appreciate some help on how to do that.

---

### Post by Sarmacid on 2008-12-19
Bump!

---

### Post by decoherence on 2008-12-19
you say it has an ethernet card... i'll assume there's some reason you can't use it...

we need to know what kind of adapter it is in order to guess what might be wrong with it.

Plug in the non-working adapter and run

```
sudo lshw -C network
```

and paste the output here. That will tell us what kind of chipset it uses and what kind of driver the kernel thinks it should have and we can go from there.

---

### Post by porchrat on 2008-12-19
> What I've tried so far have been a couple of USB-RJ45 adapters

Your server has an ethernet card, but no RJ45 port?  Wicked

> I tried assigning it a different ip an later a different MAC but kept getting errors.

What errors did you get?

---

### Post by Sarmacid on 2008-12-19
It does have 1 ethernet card with RJ45 port but I cannot use it.

the output of sudo lshw -C network for the adapter was```
*-network DISBALED
description: Etherenet interface
physical id: 2
logical name: usb0
serial: ff:ff:ff:ff:ff:ff
size: 10MB/s
capacity: 100MB/s
capabilities: ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration autonetotiation=on broadcast=yes driver=dm9601 driverversion=22-Aug-2005 duplex=half firmware=Davicom DM9601 USB Ethernet link=no multicast=yes port=MII speed=10MB/s
```

Ouput of lsusb```
Bus 001 Device 002: ID 0a46:9601 Davicom Semiconductor, Inc.
```

output of ifconfig usb0 172.16.1.1 netmask 255.255.255.0```
SIOCSIFFLAGS: Invalid argument
```

Output of ifconfig usb0 up```
usb0: ERROR while getting interface flags: No such device
```

I guess the driver is loading since I see this line in dmesg```
usbcore: registered new interface driver dm9601
```

*EDIT*
Just tried changing the MAC again and it worked, must have made a typo before >_> After changind it I don't get the ifconfig errors, I can assing an ip and bring it up but it's still not working, tried some pings and nothing, the pings worked bringing up the other interface so I know the problem is in the adapter.

---

### Post by decoherence on 2008-12-19
unplug the thing, then run

```
sudo udevadm monitor
```

then plug the device back in. give it a few seconds to run through its tasks, then post the output here.

you'll have to CTRL C to get out of udevadm.

from what I've read, this device 'should' work out of the box with 8.04

---

### Post by halitech on 2008-12-19
a network adapter with a MAC address like yours
```
MAC was ff:ff:ff:ff:ff:ff
```
means one of 2 things, drivers screwed up and is not reading it correctly or there is a problem with the card. The MAC should never show that address if it is working correctly. I had a wireless card do the same thing and turned out to be the driver was not installed properly.

---

### Post by hatten on 2008-12-19
> **Sarmacid said:**
> 
*EDIT*
Just tried changing the MAC again and it worked, must have made a typo before >_> After changind it I don't get the ifconfig errors, I can assing an ip and bring it up but it's still not working, tried some pings and nothing, the pings worked bringing up the other interface so I know the problem is in the adapter.
you must have missed his edit.

---

### Post by Sarmacid on 2008-12-19
After running udevadm monitor, I'll only post some of the output since I can't copy/paste

```
udevmonitor will print the recieved events for:
UDEV the event which udev sends out after rule processing
UEVENT the kernel uevent

UDEV [1229680380.687368] add /devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb1/1-1 (usb)
UDEV [1229680380.687426] add /devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb1/1-1/usb_endpoint/usbdev1.5_ep00 (usb_endpoint)
UDEV [1229680380.687443] add /devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb1/1-1:1.0 (usb)
...
UDEV [1229680380.699274] add /devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb1/1-1/1-1:1.0/usb_endpoint/usbdev1.5_ep81 (usb_endpoint)
...
UDEV [1229680380.772597] add /devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb1/1-1/1-1:1.0/net/usb0 (net)
...

```

The other lines are the same or very similar to the ones I posted, but now I'm starting to think the effing thing is just broken. Tried it on a windows box and had no link, same MAC I got initially.

---

### Post by halitech on 2008-12-19
> **hatten said:**
> you must have missed his edit.

no, I seen it but changing something that isn't working is not going to help. the MAC address is physically hardcoded to the card and simply trying to spoof it into thinking it is something else is like saying my alternator in my car is dead so now I'm saying it is a starter, doesn't resolve the original problem.

---

### Post by Sarmacid on 2008-12-19
Thanks to everyone that wasted their time with me, just went a bought a new one and it worked >_> The one I was using before was damaged.

---

