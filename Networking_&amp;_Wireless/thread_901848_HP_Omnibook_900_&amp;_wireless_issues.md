---
title: "HP Omnibook 900 &amp; wireless issues"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by habari on 2008-08-26
I have successfully installed hardy and enabled wireless networking through USB, PCI, PCCard with or without ndiswrapper on a variety of hardware but this one has been eluding me for a while.

I have a HP Omnibook 900 laptop with plenty of RAM (340MB) and disk space.

My wired Ethernet PCcard works fine.
I have a couple of wireless cards (airlink, linksys (I think v 3.1, based on the broadcom BCM43xx chipset) ).

The problem I am having is that wicd hangs after it starts up, the gui most of the time remains blank. Or when I select 'settings', the settings dialog box just hangs, forcing me to forcibly kill wicd.

When i play around with iwconfig, I can see that the cards are picking up the available wireless lans. I think I even managed to connect to them but they will never check out a DHCP lease, even hard coding the IP address does not solve the problem.

It seems like there is something that is getting hung up at the lower levels (hence the wicd issue) but I have no clue where to look at this point.
If anybody has any suggestions on tracing the issue that would much appreciated.

I will post more information (e.g. iwconfig output) once I have again access to the computer.

---

### Post by Crafty Kisses on 2008-08-26
Post the following output:
```
lshw -C network
```

---

### Post by habari on 2008-08-26
Here is the output of lshw -C network

>   *-network               
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 02
       serial: 00:1a:70:e0:ae:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,10/12/2006, 4.100. latency=64 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g


Here is the output of iwconfig -v

> iwconfig  Wireless-Tools version 29
          Compatible with Wireless Extension v11 to v22.

Kernel    Currently compiled with Wireless Extension v22.

wlan0     Recommend Wireless Extension v18 or later,
          Currently compiled with Wireless Extension v22.

Here is the output of iwconfig

> wconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"Dark Avenger 2"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:16:B6:4A:7D:2B   
          Bit Rate=54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:64/100  Signal level:-55 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The Access point matches with my wireless router, so it can see the router.

The output of ifconfig is

> wlan0     Link encap:Ethernet  HWaddr 00:1a:70:e0:ae:96  
          inet6 addr: fe80::21a:70ff:fee0:ae96/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:1012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1107 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114356 (111.6 KB)  TX bytes:151901 (148.3 KB)
          Interrupt:10 Memory:24000000-24002000 

wlan0:avahi Link encap:Ethernet  HWaddr 00:1a:70:e0:ae:96  
          inet addr:169.254.9.65  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Memory:24000000-24002000 

It looks like it did not check out a DHCP IP address (192.168.1.xxx on my network)

In the past I have played around with starting and stopping the dhcp client to no avail.

Is there a way to run wicd in some kind of debug mode so it will tell me where it fails or hangs?

---

