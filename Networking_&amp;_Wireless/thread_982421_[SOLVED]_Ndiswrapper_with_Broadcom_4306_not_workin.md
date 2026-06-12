---
title: "[SOLVED] Ndiswrapper with Broadcom 4306 not working"
date: 2008-11-14
forum: Networking &amp; Wireless
---

### Post by Altay_H on 2008-11-14
I followed [this guide]("http://ubuntuforums.org/showthread.php?t=201902") to get my Broadcom 4306 wireless card working again and now have ndiswrapper working, but still no wireless. When I first installed Hardy, the previously mentioned guide worked for my hardware. Now I can't get it to work with my Hardy partition or my clean install Intrepid partition. nmapplet lists no wireless networks, and iwlist wlan0 also sees no wireless networks. I am certain, however, that I'm within range of at least 4 wireless networks.

Here's my output for ndiswrapper -l:
```

:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

```

And my output for ifconfig -a:
```

:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:70:a3:47  
          inet addr:10.24.102.203  Bcast:10.24.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:b0ff:fe70:a347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:792309 (792.3 KB)  TX bytes:178532 (178.5 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30456 (30.4 KB)  TX bytes:30456 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr b2:75:54:56:27:6d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:eb:3c:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-EB-3C-8A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And my output for iwlist scanning:
```

~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

I'm not sure what wmaster0 or pan0 are, considering I only have one wireless card and one ethernet port. When I first installed Hardy I only had lo, eth0, and wlan0. I messed around with my wireless configuration trying to get aircrack working, and after a brief success ended up with messed up wireless settings. I decided to do a clean install of Intrepid Ibex, figuring it would leave me with just lo, eth0, and wlan0 again, but pan0 and wmaster0 are still there. Maybe they're supposed to be there, but I can't help noticing that the presence of pan0 and wmaster0 have resulted in no wireless for me. Any help is greatly appreciated.

---

### Post by Ayuthia on 2008-11-14
> **Altay_H said:**
> I followed [this guide]("http://ubuntuforums.org/showthread.php?t=201902") to get my Broadcom 4306 wireless card working again and now have ndiswrapper working, but still no wireless. When I first installed Hardy, the previously mentioned guide worked for my hardware. Now I can't get it to work with my Hardy partition or my clean install Intrepid partition. nmapplet lists no wireless networks, and iwlist wlan0 also sees no wireless networks. I am certain, however, that I'm within range of at least 4 wireless networks.

Here's my output for ndiswrapper -l:
```

:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

```

And my output for ifconfig -a:
```

:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:70:a3:47  
          inet addr:10.24.102.203  Bcast:10.24.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:b0ff:fe70:a347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2321 errors:0 dropped:0 overruns:0 frame:0
          TX packets:730 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:792309 (792.3 KB)  TX bytes:178532 (178.5 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30456 (30.4 KB)  TX bytes:30456 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr b2:75:54:56:27:6d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:eb:3c:8a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-EB-3C-8A-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And my output for iwlist scanning:
```

~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

```

I'm not sure what wmaster0 or pan0 are, considering I only have one wireless card and one ethernet port. When I first installed Hardy I only had lo, eth0, and wlan0. I messed around with my wireless configuration trying to get aircrack working, and after a brief success ended up with messed up wireless settings. I decided to do a clean install of Intrepid Ibex, figuring it would leave me with just lo, eth0, and wlan0 again, but pan0 and wmaster0 are still there. Maybe they're supposed to be there, but I can't help noticing that the presence of pan0 and wmaster0 have resulted in no wireless for me. Any help is greatly appreciated.

Please try the following:
```
sudo modprobe -r b43legacy b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan
```

This will remove all the possible wireless drivers for your card and then load ndiswrapper.  It will then scan for wireless sites.  This will only work for this session though.

---

### Post by Altay_H on 2008-11-15
> **Ayuthia said:**
> Please try the following:
```
sudo modprobe -r b43legacy b43 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo iwlist scan
```

That didn't work. All it did is remove the wireless option from nmapplet and remove wlan0 from ifconfig. Here's the output:

```
:~$ sudo modprobe -r b43legacy b43 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.
:~$ sudo modprobe ndiswrapper
:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

And now the output for ifconfig -a is:
```
:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:70:a3:47  
          inet addr:10.24.102.203  Bcast:10.24.255.255  Mask:255.255.0.0
          inet6 addr: fe80::20f:b0ff:fe70:a347/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2631 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2354303 (2.3 MB)  TX bytes:352797 (352.7 KB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30456 (30.4 KB)  TX bytes:30456 (30.4 KB)

pan0      Link encap:Ethernet  HWaddr b2:73:7f:61:4b:2e  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by Altay_H on 2008-11-18
Bump.

Still no luck. Any ideas?

---

### Post by Ayuthia on 2008-11-18
> **Altay_H said:**
> That didn't work. All it did is remove the wireless option from nmapplet and remove wlan0 from ifconfig. Here's the output:

```
:~$ sudo modprobe -r b43legacy b43 ssb ndiswrapper wl bcm43xx
FATAL: Module ssb is in use.

```

This means that another module is using ssb.  Try the following instead:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
sudo modprobe ndiswrapper
sudo modprobe b44
sudo ifconfig eth0 up
sudo iwlist scan
```

---

### Post by Altay_H on 2008-11-18
> **Ayuthia said:**
> This means that another module is using ssb.  Try the following instead

Excellent, it worked. How can I make it permanent?

Also, why did it work? I'm familiar with iwlist and ifconfig, but I'm not familiar with modprobe. I realize modprobe adds/removes modules from the kernel, but what's a module?

Here's the output, irrelevent though it is.
```

:~$ sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
FATAL: Module bcm43xx not found.
:~$ sudo modprobe ndiswrapper
:~$ sudo modprobe b44
:~$ sudo ifconfig wlan0 up

```

---

### Post by Ayuthia on 2008-11-18
> **Altay_H said:**
> Excellent, it worked. How can I make it permanent?

Also, why did it work? I'm familiar with iwlist and ifconfig, but I'm not familiar with modprobe. I realize modprobe adds/removes modules from the kernel, but what's a module?

Here's the output, irrelevent though it is.
```

:~$ sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
FATAL: Module bcm43xx not found.
:~$ sudo modprobe ndiswrapper
:~$ sudo modprobe b44
:~$ sudo ifconfig wlan0 up

```

What is happening is that you have some wireless modules that are currently loaded that is conflicting with ndiswrapper.  The modprobe command loads and unloads (modprobe -r) kernel modules.  It looks like you also have the b44 module (the Broadcom driver for your wired card).  You might try this first (it comes from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3):](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3):)
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb wl; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper 
```

Hope that helps.

---

### Post by wolfmaniac on 2008-11-19
I had the exact problem....

And your solution worked for me.

Thank you very much.

NB I am using Mint Elyssa.

---

### Post by Altay_H on 2008-12-11
I'm having this problem again. This time I can't seem to changed the module.

```

:~$ sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper wl bcm43xx
FATAL: Module bcm43xx not found.
:~$ sudo modprobe ndiswrapper
:~$ sudo modprobe b44
:~$ sudo lshw -C network
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:03:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:70:a3:47
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.24.102.226 latency=128 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: b6:fb:e4:32:5b:ff
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:eb:3c:8a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

Even after I remove ssb and put ndiswrapper and b44 in its place, ssb remains the loaded module. Any ideas?

---

### Post by Altay_H on 2008-12-11
Strangely this issue resolved itself the same way it was caused. My wireless stopped working, as I posted above, when I was trying to get rtcwake to work and I suspended my computer. I was recently trying to get rtcwake to work again and when I suspended this time it started working again. I'm not sure if it's related, but it's solved. At least for now.

---

