---
title: "Wireless Performing Poorly"
date: 2015-04-20
forum: Networking &amp; Wireless
---

### Post by newb85 on 2015-04-20
All right, I've been using Ubuntu for several years, and this is the first networking issue I've had in almost as many.

The laptop I'm using I've been running with Ubuntu for 3 1/2 years.  I've changed nothing in the hardware.  Just recently, though, the wireless performance started slowing.  I can't figure out where the problem is.  If I take it into the garage (where the router is), I get over 7Mbps.  Sitting in the living room (where it has lived for two years), I get about .3 Mbps.  My wife's machine (sitting next to it and sadly, running Windows) still gets over 4Mbps.  My android phone works great, too.

If I try pinging google or even the router, I have serious packet loss.

I have rebooted the router.  Doesn't seem to help.

I tried booting to an older kernel.  Doesn't seem to make a difference (unless I didn't go old enough...)

---

### Post by newb85 on 2015-04-20
Oh, and here's this.  Never had to do anything fancy with it.
```

  *-network
       description: Wireless interface
       product: Centrino Wireless-N 1000 [Condor Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:06:ed:ee
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-48-generic firmware=39.31.5.1 build 35138 ip=192.168.0.102 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:48 memory:f7e00000-f7e01fff

```

---

### Post by jeremy31 on 2015-04-20
Run the wireless script from [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108) and post the results.  Hopefully it will show what is wrong

---

