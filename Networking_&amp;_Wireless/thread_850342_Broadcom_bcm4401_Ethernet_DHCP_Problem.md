---
title: "Broadcom bcm4401 Ethernet DHCP Problem"
date: 2008-07-05
forum: Networking &amp; Wireless
---

### Post by akessler on 2008-07-05
I have a Dell Inspiron B130 laptop, which has a Broadcom BCM4401-B0 100Base-TX ethernet controller. I've been able to get the wireless card to work, but I've never been able to get the wired interface to work.
In addition, I have a number of interesting messages in my dmesg (eth0: link is not ready).
```

# dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6983
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:14:22:91:d8:13
Sending on   LPF/eth0/00:14:22:91:d8:13
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```

$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:14:22:91:d8:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 
```
```

$ dmesg | grep eth0
[   12.568170] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:91:d8:13
[   26.072543] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:91:d8:13
[   31.305809] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:14:22:91:d8:13
[   46.765565] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.774665] ADDRCONF(NETDEV_UP): eth0: link is not ready
```
I have the b44 and ndiswrapper modules loaded.
```

$ lspci -nn | grep -i bcmlspci -nn |grep -i bcm4401
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
```
```

$ ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:170C) present (alternate driver: b44)
        device (14E4:4318) present (alternate driver: bcm43xx)
```
Has anyone encountered a similar problem? Any ideas on how to fix it?

---

### Post by akessler on 2008-07-05
bump

---

### Post by dcherryholmes on 2008-07-15
And bump again.  The official Ubuntu docs say it is autodetected and supported, but it is not for me.

[https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsBroadcom](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsBroadcom)

I'm trying to get an Inspiron 5100 working.

---

### Post by iris-n on 2008-07-19
Mr. Holmes,

It would seem to me that as you have both drivers installed, they are conflicting. The fact that it shows up three times hints that it is being detected more than once. I have the exact same card as yours, on a Latitude 120l, and i managed to make it work just by enabling the b44 driver. Would you try removing ndiswrapper to see if it does the trick?

Yours,

Iris

---

### Post by leberknight on 2008-08-06
Greetings,
I have the same problem, but ndiswrapper is NOT installed.
lshw -C network tells me:
 I'm using BCM4401-B0 for eth0
 link=no !!!
My linux kernal is version 2.6.24-19-generic
dmesg says, "link is not ready"
I'm out of ideas.
No link means no ethernet.
Ethernet=good!!!
Please help.
Thanks,

---

### Post by genchaos55 on 2009-05-12
i'm having the exact same problem.
can't seem to find any good answers on the web/forums.
broadcom 44xx is def unhappy with ubuntu.
any help would be greatly appreciated.
currently using/trying to use ubuntu 9.04 desktop i386.

---

### Post by Ukemi on 2009-06-19
bump

I am experiencing the same problem, and have not been able to find any answers on these forums (or anywhere on the net).

I've installed Jaunty Jackalope (server edition) onto my Dell Inspiron 600m, and have not been able to connect to ethernet. Trying # dhclient eth0, $ ifconfig eth0, and $ dmesg | grep eth0, I recieve messages nearly identical to those posted by the original poster (akessler). I also experience lshw -C network --> "link=no" and dmesg --> "link is not ready" like leberknight.

Is there no solution to this problem? I have tried installing different versions of Ubuntu on this (my spare, old) computer mutliple times over the last 2-3 years, and this particular issue seems to be the only thing preventing me from trying out Ubuntu.

---

### Post by starr0stealer on 2009-08-15
Im getting into this issue, had issues getting ubuntu on a Optiplex 320
I'm in the live CD and it uses the network card. So that means it can work right?

In live boot, this is what I get on these commands

```
clear; dmesg | grep eth0; lspci | grep net
[    6.533130] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:1b:2c:6f
[  129.553193] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  132.804188] b44: eth0: Link is up at 100 Mbps, full duplex.
[  132.804193] b44: eth0: Flow control is off for TX and off for RX.
[  132.804519] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  143.456259] eth0: no IPv6 routers present
02:09.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:1b:2c:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.7 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:7f:93:97:22:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

---

### Post by starr0stealer on 2009-08-15
Odd, I rebooted and my network card works fine. Ubuntu seems to have no issues with it at. ( 9.04 ).

```

[    6.441862] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:1b:2c:6f
[   21.524504] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.804184] b44: eth0: Link is up at 100 Mbps, full duplex.
[   24.804188] b44: eth0: Flow control is off for TX and off for RX.
[   24.804511] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.164012] eth0: no IPv6 routers present
02:09.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


AND 


  *-network               
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:1b:2c:6f
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.2.7 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:19:ff:a1:8c:54
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by Blender Can Do Anything on 2009-08-21
HOW TO GET THE BROADCOM BCM4401 WORKING

I fought this issue for quite a while and solved it! (kinda proud there. First big thing to do with ubuntu, but hey)

if it is not working, it likely means there are two drivers running at the same time. the two drivers conflict and refuse to let it run

so. to fix this, you need to know what drivers are running.

"ndiswrapper -l"

it will display what driver you have running. In my case, because I was following other help forums ([http://ubuntuforums.org/archive/index.php/t-511343.html](http://ubuntuforums.org/archive/index.php/t-511343.html)), it said

"b44win : driver installed
	device (14E4:4401) present (alternate driver: b44)"

Also, according to Ubuntu ([https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)) there are a bunch of drivers which should not be running. They are:

"bxm43xx
b43
b43legacy
ssb"

I added 'b44' to the list. I don't know if it should/should not be on the list because I had installed a windows wireless card driver

so, take these and add them to the bottom of the text file located at:
/etc/modprobe.d/blacklist.conf

Add to the end of the text file:

"# my changes
blacklist b44
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb"

If (as I was/am) and don't know how to change text files outside of the terminal, use this. I have been told not to use this (by linux friends) many a time.

"gksudo nautilus"

It opens a GUI window where you can modify anything as root. Go to the file, change it, save it, restart.

It was a fun 8 hour fight! Good luck!

---

