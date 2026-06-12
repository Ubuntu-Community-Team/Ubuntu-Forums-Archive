---
title: "USB Wifi Adapter - Panda PAU05 - Ralink RT 5372 Suddenly Stopped Working - 16.04"
date: 2016-08-01
forum: Networking &amp; Wireless
---

### Post by joelbitar1986 on 2016-08-01
Hello,

Upon freshly installing Ubuntu 16.04, my Panda PAU05 USB Wifi Adapter was working out the box on the  freshly installed OS. It has been working for about 2 months until yesterday,  when it suddenly stopped working. It is currently recognized as a USB  device on my system. However, my network manager does not recognize the  USB wifi adapter as a network device and no longer allows me to access  the internet. When I type in `lsusb` It appears as: 

```
Bus 001 Device 002: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
```

The **one **thing I accidentally changed was the  blacklisted drivers listed at the bottom of  /etc/modprobe.d/blacklist.conf. Is it possible that this could be the  culprit? Would anyone mind sharing the default blacklisted drivers in  that file for Ubuntu 14.04-16.04? Maybe if I revert to them my device will be recognized.

I also tried installing the drivers for my device on this site: [http://www.mediatek.com/en/downloads1/downloads/?sort=os](http://www.mediatek.com/en/downloads1/downloads/?sort=os)

When I build those drivers I get the following error: 

```
Makefile:1403: recipe for target '_module_/home/joel/Downloads/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux' failed
make[1]: *** [_module_/home/joel/Downloads/DPO_RT5572_LinuxSTA_2.6.1.3_20121022/os/linux] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-31-generic'
Makefile:388: recipe for target 'LINUX' failed
make: *** [LINUX] Error 2
```

Any help appreciated to get this wifi adapter back running.

---

### Post by Bucky Ball on 2016-08-01
No point in building/installing the drivers from a third-party site when the device was working 'out of the box' with the open-source ones, which are probably still installed. This could add more confusion to the mix.

Please give the output, in code tags, of this command, please:

```
sudo lshw -C network
```

Can you go back and reverse the changes you made in whatever files you made them in? Always a good idea to make a backup of the original file before tweaking it ...

By the way, I presume you completely deleted the entries in the blacklist file rather than 'hashing' them out? Rather than kill lines totally, simply put a # in front of the line. That will prevent it being read and acted upon. For instance ...

```
blacklist pcspkr
```

... becomes

```
# blacklist pcspkr
```

If you then need to revert the changes, always a good idea if they didn't work, just remove the #.

---

### Post by praseodym on 2016-08-02
```
modprobe -c | grep -i '148f.*5372'
alias usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in* rt2800usb
```
Should work ootb.
```

sudo modprobe -v rt2800usb
```

---

### Post by joelbitar1986 on 2016-08-02
@BuckyBall

So one of those weird Linux things.. I turned my computer on today and the wifi adapter is working all of a sudden. However, the name of it is no longer being recognized by Network Manager.

sudo lshw -C network

```
*-usb:0                 
       description: Wireless interface
       product: 802.11 n WLAN
       vendor: Ralink
       physical id: 3
       bus info: usb@1:3
       logical name: wlx9cefd5ff416f
       version: 1.01
       serial: 9c:ef:d5:ff:41:6f
       capabilities: usb-2.00 ethernet physical wireless
       configuration: broadcast=yes driver=rt2800usb driverversion=4.4.0-31-generic firmware=0.29 ip=100.65.0.130 link=yes maxpower=450mA promiscuous=yes speed=480Mbit/s wireless=IEEE 802.11bgn
  *-network
       description: Wireless interface
       product: Wireless 7265
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 59
       serial: 00:21:5c:b6:0b:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-31-generic firmware=16.242414.0 ip=10.21.173.239 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:128 memory:dfa00000-dfa01fff
```


But it's working as before, so I'm content. You are indeed correct that I deleted an entry rather than just comment it out. Thanks for the advice moving forward.

@praseodym: I entered those commands anyway, everything seems to be running smoothly.

---

