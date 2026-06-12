---
title: "All Internet Works But Wirelesss Intranet Broken"
date: 2008-02-22
forum: Networking &amp; Wireless
---

### Post by Mariner_Overseas on 2008-02-22
Hello,

At my wits end after hours of searching and testing. ](*,)  First post, be gentle.

Building a MythTV box (Mythbuntu 32 bit v7.10; 2.6.22-14-generic with Desktop added subsequently).

Motherboard ethernet (eth0; static 192.168.1.151) works perfectly - connects to internet and can ping router (WRT54-GS; 192.168.1.1) and other intranet machines.

The WPA WLAN (wlan0; DHCP 191.168.1.102; USB D-Link DWL-G122) has no problem connecting to internet through this same router, but will not ping the IP address of the router or other intranet computers (host unreachable) - Likewise, other intranet computers are unable to ping the  WLAN IP address, but have no problem pinging this crate through its ethernet port.

My Windows laptop's built-in wireless will successfully ping the router and another (non-MythTV) Unbuntu desktop (which is ethernet to the router) so it's not something inherent to wireless or my router that's keeping me from pinging my intranet to/from the Myth box.

So far as I am aware, my router is not filtering on mac's or other characteristics, and I've used this same USB 802.11G device successfully with a Windows laptop and a Wii game console to connect to the internet through this same router (though have not tested pinging with these other devices).

I've tried using Wicd instead of Network-Manager but didn't have any better luck - Hope that wasn't because I was so damned tired...

The ultimate goal is to get ssh working wirelessly so I could install this 80% operational crate in the living room, while continuing to tweak remotely.  When ssh commands failed to connect, I discovered the ping issue which I believe to be at the root of my problem.

Thank you for any suggestions.


```
user@computer:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.153  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0x4000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:254 errors:0 dropped:0 overruns:0 frame:0
          TX packets:254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28590 (27.9 KB)  TX bytes:28590 (27.9 KB)

wlan0     Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::219:5bff:fed3:58b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9259486 (8.8 MB)  TX bytes:1571578 (1.4 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-5B-D3-58-B1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```

```
user@computer$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=192.168.1.153 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: xx:xx:xx:xx:xx:xx
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.102 multicast=yes wireless=IEEE 802.11g
```

```
user@computer$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.153
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0
```

---

### Post by Mariner_Overseas on 2008-03-14
Given the dearth of suggestions and my lack of progress in any event, I took an entirely different tack.

I purchased a second WRT54GS wireless router which had been flashed with DD-WRT v24 firmware, and set up a wireless bridge.

Now the MythTV crate, two game consoles, and a laptop each enjoy an “Ethernet island" and I've managed to avoid the connectivity anomalies that were driving me crazy when I first posted.

Whether the D-Link DWL-G122 USB wireless was at fault or I’ve changed something else in the intervening three weeks that fixed my issue, I’ll never know.

I'm now using Xming and PuTTY to remote view select Ubuntu video output on my Windows laptop so maybe my family can start enjoying MythTV on the big screen even as I continue to (remotely) resolve my outstanding issues (like how the %$*! am I supposed to get PVR-150 capture card audio ported out the embedded TOSLINK on my ANM2HD mobo?  And why did the machine suddenly stop recognizing the DVD drive?  And how does this damned IR blaster work?  And what about this iMON display?).

Oh, the fun never ends...

---

