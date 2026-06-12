---
title: "Belkin F5D9010 Notebook Card Help"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by lilgoo19 on 2008-07-01
well, last night my windows crashed, so long story short i decided to switch to ubuntu for the first time. So far im amazed, the only problem is that my Belkin F5D9010 notebook card will not work. 
I have no linux experience, so you may have to baby it for me.
Can anyone help, it would be greatly appreciated.
oh, and it is recognized by the system, it just shows no wireless networks

---

### Post by chili555 on 2008-07-01
I believe there are several versions of this card, and some do not have the same chipset. Let's check. Please open Applications -> Accessories -> Terminal and type:```
sudo lshw -C network
iwconfig
```Post the result here and we'll be glad to help you.

---

### Post by agarzon on 2010-01-21
I have the same problem. I already tried:

```

sudo depmod -a
sudo modprobe ndiswrapper
ndiswrapper -i NetAni.inf

```

and the driver appears installed but the network interface is not found:

```

ndiswrapper -l
netani : driver installed
	device (17CB:0001) present (alternate driver: agnx)

```

When I run the command you recommended I get

```

agarzon@IBM-laptop:~$ sudo lshw -C network
[sudo] password for agarzon: 
  *-network               
       description: AG100 Wireless Lan Adapter
       vendor: Airgo
       physical id: 0
       slot: Socket 1
       resources: irq:11
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:8f:50:c7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.0.11 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:f4120000-f4120fff ioport:1800(size=64) memory:f4100000-f411ffff memory:30100000-301fffff(prefetchable)
  *-network DISABLED
       description: interface
       product: AGN100 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 1
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 01
       serial: 00:11:50:2d:ed:53
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical
       configuration: driver=agnx-pci latency=248 maxlatency=255 mingnt=24
       resources: irq:11 memory:2c080000-2c09ffff memory:2c000000-2c07ffff

```

and iwconfig returns:


```

agarzon@IBM-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wmaster0  no wireless extensions.


```

I am running the Belkin F5D9010 on an IBM laptop. (PCMCIA wireless card). I am using 9.10 32bit

---

### Post by Razz27 on 2010-03-14
Hi all,

I got the exact same problem as agarzon up there.  exact same output as well.  Scouring google about this network card hasn't revealed too much, so if there are any experts around, your help would be appreciated.  Seems to me like it's just a case of "Enabling" the device, somehow.  Ndiswrapper has loaded all the drivers correctly, and so the only problem seems to be in that output of lshw, where the Wireless Card network interface is DISABLED.

-Razz27

PS: hope this old post gets some attention, cus it looks like this is still an issue

---

### Post by love_the_idle_life on 2011-02-03
Hi :)

i have the same problem with my pcmcia wlan-card. is there anybody out there with an idea? Please i need help


```

lshw -c network

  *-network DISABLED
       description: interface
       product: AGN300 802.11 a/b/g True MIMO Wireless Card
       vendor: Airgo Networks Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 04:04:f7:01:06:05
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical
       configuration: driver=agnx-pci latency=248 maxlatency=255 mingnt=24
       resources: irq:9 memory:14080000-1409ffff memory:14000000-1407ffff

```

```

lspci -v

01:00.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)
	Subsystem: Netgear Device 6d00
	Flags: bus master, medium devsel, latency 248, IRQ 9
	Memory at 14080000 (32-bit, non-prefetchable) [size=128K]
	Memory at 14000000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: agnx-pci
	Kernel modules: agnx

```

```

ifconfig -a

wmaster0  Link encap:UNSPEC  HWaddr 04-04-F7-01-06-05-30-30-00-00-00-00-00-00-00-00  
          [NO FLAGS]  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

iwconfig

wmaster0 no wireless extensions.

```

---

### Post by dalzmc on 2011-12-23
i am having the same problem.  i am on ubuntu 11.10 and belkin F5D9010,  i can see the networks, it notices it, but WPA and WPA2 just are NOT working. is it the drivers? the setup cd does not work...

---

### Post by chili555 on 2011-12-23
> but WPA and WPA2 just are NOT working.Can you reset your router to WPA2 *only*? Some drivers have difficulty with mixed-mode WPA and WPA2.

---

