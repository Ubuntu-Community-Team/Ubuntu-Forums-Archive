---
title: "Router"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Robert1305 on 2011-05-24
When I take my laptop downstairs The wi-fi connection shows 3bar reception, but, after 10 or so minutes it drops connection, but my desktop is still connected, which is hard wired to the router.

The laptop is directly beneath the router with only the wooden floor boards between the router and my laptop.

Is there any way I can improve reception.

Thanks.

---

### Post by Rex Bouwense on 2011-05-24
I don't think that it has anything to do with your operating system.  It is probably just a quirk of the wireless.  You can add a remote access point to your system.  That is what we did at a campground to increase the range of the router.  It is odd however that you lose the signal with only floor boards separating you from the router.

---

### Post by Peter09 on 2011-05-24
Can you post the output of
 
```
lshw -C network
```

---

### Post by Robert1305 on 2011-05-24
robert@robert-System-Product-Name:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:1a:92:21:df:ae
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.2 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:fbcfc000-fbcfffff ioport:c800(size=256) memory:fbcc0000-fbcdffff
  *-network
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 4
       bus info: pci@0000:07:04.0
       logical name: eth1
       version: 14
       serial: 00:1a:92:21:ce:de
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=64 maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:19 memory:fbff4000-fbff7fff ioport:e800(size=256) memory:fbfc0000-fbfdffff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:15:af:0e:06:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.38-8-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
robert@robert-System-Product-Name:~$

Would give my right arm to understand this.

---

### Post by crispy_420 on 2011-05-24
You would be surprised what can be in a wall/floor. Many homes were not designed with wifi (or any wireless) in mind. In fact it may not even be a thought. There could be lots of stuff in the floor to ruin signal. Where I live I am convinced builders look for ways to ruin wireless. One place I lived I had to go into the backyard to use my cell phone.

But on a side note, does it ever happen on the same level?

Or even a hardware problem? Wifi card issue or router failing? Had Netgear router that worked most of the time then would randomly require a reset.

---

### Post by 5149.5 on 2011-05-24
You could run nm-tool to see what your local wireless environment looks like. It will show other wireless APs that you are receiving with their channel and signal strength information. Sometimes you can get a little more performance by moving your channel to one that is unused by adjacent APs.

---

### Post by Peter09 on 2011-05-24
Yes -this driver has a bug which does as you describe,
try

[http://forum.aircrack-ng.org/index.php?topic=5755.0](http://forum.aircrack-ng.org/index.php?topic=5755.0)

see if this helps

---

