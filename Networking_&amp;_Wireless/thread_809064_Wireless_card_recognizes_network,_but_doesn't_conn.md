---
title: "Wireless card recognizes network, but doesn't connect"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by bryan6376 on 2008-05-27
Hey all,

Just installed Heron (8.04), and am connected via ethernet cable.  Downloaded all the updates, and was thrilled to have it recognize my wireless card.  I'm running a WMP54G wireless card, which previously had problems in older versions of Ubuntu, but seems to be supported now.  It's a bcm4306 chipset, and was curious if one of you could troubleshoot for me.  I can see my wireless network, but it won't let me connect to it.  Attempting to just gives me the two blue balls and a green "loading" circle through them until it times out.

I already enabled the chipset in the System->Admin->Hardware Drivers.

Here's my ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:19:d1:1a:5b:7a  
          inet addr:192.168.123.109  Bcast:192.168.123.255  Mask:255.255.255.0
          inet6 addr: fe80::219:d1ff:fe1a:5b7a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13314 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17570154 (16.7 MB)  TX bytes:1131899 (1.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98700 (96.3 KB)  TX bytes:98700 (96.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0f:66:6f:e8:56  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0F-66-6F-E8-56-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


And here's my lshw -C network:

 *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:07:08.0
       logical name: eth0
       version: 01
       serial: 00:19:d1:1a:5b:7a
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.123.109 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0f:66:6f:e8:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


Any suggestions on why it's not connecting to my wireless?  Should I just try a manual config of my wireless settings, inputting an IP address and all that jazz?

Thanks for your time!

---

### Post by bryan6376 on 2008-05-27
Alright, so I finally got this working.  I have a bcm4306 ver 03 card.  Now, I wasn't able to do it with my current setup, but I did a complete re-install of Heron and here's what I did:

First, I downloaded all updates...duh

Second, I did NOT use the driver in the System->Admin->Hardware Drivers.  I did NOT use it, to repeat.

Third, I went to this post: [http://ubuntuforums.org/showthread.php?t=766560](http://ubuntuforums.org/showthread.php?t=766560)

Following his steps, I was able to get it to work.  However, in his Step 2, I clicked on the link under the read font, and used step 2b there.  I literally copied and pasted every command into the terminal, restarted, and it worked.  This is using Heron x.xx.17, from scratch, so it should work for you!  Don't forget to restart!

---

