---
title: "Netgear WNDA3100, lost with update"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by Miles_Militis on 2010-05-27
Hello all,

I recently downloaded and installed a dual boot of Ubuntu 10.04 along with my current OS Windows7.  Initially it detected my wireless device (Netgear wireless USB adapter Model: WNDA3100), but after downloading and installing updates per the request of Ubuntu's update manager; I seem to have lost functionality. Before all I had to do was plug it in and everything worked just fine, but now Ubuntu won't even recognize that its plugged in.

Is there a way to get that functionality back?  I would imagine there is, but I'm still pretty new around linux.

---

### Post by -humanaut- on 2010-05-27
When you click on the network manager Icon is there any option for it? or is there just the Wired Auto-Eth0 option?

---

### Post by Miles_Militis on 2010-05-27
There is an option to enable wireless, but Ubuntu won't let me click it.

---

### Post by -humanaut- on 2010-05-27
Alright, well atleast it sounds like its detecting its there. can you type: ifconfig -a

from a terminal and post back please? also try alt+f2 and type gtk-jockey and see if theres a driver available for it.

---

### Post by Miles_Militis on 2010-05-27
Here is the result of "ifconfig -a"

```
eth0      Link encap:Ethernet  HWaddr 00:16:d4:2e:f2:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a5:ad:00:bd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:1e:2a:e2:76:a4  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I tried alt-F2 then "gtk-jockey" but it gave me an error saying no such directory/file.

---

### Post by Miles_Militis on 2010-05-27
I've also tried to uninstall/reinstall the proprietary wireless drivers that Ubuntu offers me in the "Hardware Drivers" menu.

---

### Post by Miles_Militis on 2010-05-29
*bump*

---

### Post by anewguy on 2010-05-29
Please post the output of:

lshw -C network

If this is a laptop, also post the output of:

lsusb


Thanks!
Dave ;)

---

### Post by Miles_Militis on 2010-05-30
Thanks for the response anewguy!

Here is the ouput to lshw -C Network

```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:21 memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:2e:f2:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:ad:00:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:1e:2a:e2:76:a4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11abg


```


and here is the output to lsusb (yes I'm running a laptop)

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9010 NetGear, Inc. WNDA3100 802.11n
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

### Post by anewguy on 2010-05-30
Ok - your wireless is the Broadcom 4318, a common adapter, and a common problem.  So a couple of questions:

- if you go to System/Administration/Hardware Drivers, does it show a driver, and if so, is it enabled?

- if you have the ability to hard-wire a connection to a router temporarily, do the following:

open a terminal window (applications/accessories/terminal)

type:

sudo apt-get update <press enter> Enter your regular password when prompted.

When that completes, check in System/Administration/Hardware Drivers for a restricted driver - if one shows enable it, then disconnect the hard-wire cable, wait a couple of minutes, then check in network manager to see if wireless networks are showing.  BTW - you may now need to click enable wireless in network manager as well.

Please post back the results and any questions!  If it doesn't help, we'll go from there to get you working.

Dave ;)

---

### Post by Miles_Militis on 2010-05-30
I booted up my laptop in Ubuntu and plugged into the router itself.  After doing what you said a new driver was downloaded and installed, but no noticeable difference.  For some reason Ubuntu won't allow me to enable wireless networking (at least through the networking icon at the top right of the screen.).

The option is there, but not click-able.

---

### Post by anewguy on 2010-06-01
Sorry for the delay - been busy enjoying the holiday.

Please post back the output of the following again:

lshw -C network

lsmod

cat /etc/modprobe.d/blacklist.conf (this will be lengthy)

Since the update, I want to see from the lshw -C network what driver is being used now, from the lsmod what kernel modules are loaded and from the cat /etc/modprobe.d/blacklist.conf the contents of the blacklisted modules file.

Thanks
Dave ;)

---

