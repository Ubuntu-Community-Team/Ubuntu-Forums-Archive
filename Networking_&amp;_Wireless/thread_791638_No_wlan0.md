---
title: "No wlan0"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by ferunandesu on 2008-05-12
Hello--

My Broadcom wireless card was working perfectly under 7.10 with ndiswrapper using the bcmwl5 driver. I upgraded to 8.04 yesterday, and it still worked, but there was a problem with hal that forced me to reinstall it. After that, the wireless no longer works. lspci shows my wireless card, but iwconfig only returns lo and eth3. I'd never seen eth3 before, so I checked the syslogs and eth0 is being renamed to eth3 by udev. Regardless, there is no wlan0. I've tried multiple times to reinstall the bcmwl5 driver with ndiswrapper, and it does so without giving any errors, but no logical name shows up for the card, no light, etc.

The really troubling part of this is that I'm travelling and I can't find a way to get a wired connection to troubleshoot. Right now, I'm on a paid terminal at a hostel.

--Thanks

---

### Post by Ayuthia on 2008-05-12
> **ferunandesu said:**
> Hello--

My Broadcom wireless card was working perfectly under 7.10 with ndiswrapper using the bcmwl5 driver. I upgraded to 8.04 yesterday, and it still worked, but there was a problem with hal that forced me to reinstall it. After that, the wireless no longer works. lspci shows my wireless card, but iwconfig only returns lo and eth3. I'd never seen eth3 before, so I checked the syslogs and eth0 is being renamed to eth3 by udev. Regardless, there is no wlan0. I've tried multiple times to reinstall the bcmwl5 driver with ndiswrapper, and it does so without giving any errors, but no logical name shows up for the card, no light, etc.

The really troubling part of this is that I'm travelling and I can't find a way to get a wired connection to troubleshoot. Right now, I'm on a paid terminal at a hostel.

--Thanks
I am not for sure if you will get this in time or not, but you might need to check and see (in the terminal) if ndiswrapper -v (shows a working version 1.50 or higher) and ndiswrapper -l shows that the driver is present.  If that is ok, the temporary way to get it up should be:
```
sudo modprobe -r b43 b44 ssb
sudo modprobe ndiswrapper
```
That will disable the native Broadcom Linux drivers and use ndiswrapper.

If that works, then you are having problems with one of the following:
blacklisting (/etc/modprobe.d/blacklist)
loading ndiswrapper at start (/etc/modules)
If you have a Broadcom wired card, you don't have a script running to load ndiswrapper before ssb.

If you do have a Broadcom wired card, the commands I gave you above will disable the card.  You should be able to get it back up by doing sudo modprobe b44.  However, these commands will only work for that session.  Once you reboot, you will have to do it again.

Hopefully, this will get you limping along until you are able to find a place to fix it.

---

### Post by ferunandesu on 2008-05-12
None of that worked, not even temporarily.


lshw -C network
```

...

description: Network controller
product: BCM94311MCG wlan mini-pci
vendor: Broadcom corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 02
width: 64 bits
clock: 33 MHz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb


```

iwconfig
```

lo        no wireless extensions

eth3      no wireless extensions

```

ndiswrapper -v
```

utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-17-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-17-generic SMP mod_unload

```

ndiswrapper -l
```

bcmwl5 : driver installed
        device (14E4:4311) present (alternate driver: ssb)

```

lscpi
```

...

03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)

```

portion for wireless card in /etc/udev/70-persistent-net.rules
```

# PCI device 0x14e4:0x4311 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}="00:1a:73:9e:51:f8", ATTRS{type}=="1", NAME="wlan0"

```

etc/modules
```

fuse
lp
rtc
sbp2
ndiswrapper

```

---

### Post by Ayuthia on 2008-05-12
> **ferunandesu said:**
> None of that worked, not even temporarily.


lshw -C network
```

...

description: Network controller
product: BCM94311MCG wlan mini-pci
vendor: Broadcom corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 02
width: 64 bits
clock: 33 MHz
capabilities: bus_master cap_list
configuration: driver=b43-pci-bridge latency=0 module=ssb


```

portion for wireless card in /etc/udev/70-persistent-net.rules
```

# PCI device 0x14e4:0x4311 (ndiswrapper)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}="00:1a:73:9e:51:f8", ATTRS{type}=="1", NAME="wlan0"

```



Sorry if I am pointing out the obvious, but it is showing that it is trying to use b43 and ssb.  The udev results show that it should be wlan0.

Did you see any messages when you did the modprobe of the modules?  If you didn't, you might check dmesg to see what it says.  You might also see if ndiswrapper loaded and b43 and ssb were removed (lsmod|grep -i -e b43 -e ssb -e ndiswrapper).

The only thing that I can see right now is that the b43 module is there and we need to figure out how to unload it.  Do you have a script that you are using to unload the b43 and ssb drivers?  I am not for sure about how you did that portion.  It could be something in /etc/init.d, /etc/rc.local, or maybe /etc/modprobe.d/ndiswrapper.  You might need to modify it.

---

