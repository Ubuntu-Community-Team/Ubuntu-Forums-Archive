---
title: "I think my ethernet connection broke my wireless"
date: 2008-09-24
forum: Networking &amp; Wireless
---

### Post by dai_vernon on 2008-09-24
After some pain, I got wireless networking to work on my Compaq Presario F700 (Atheros 5007 chipset I believe).  When I went off to college, I had the option of choosing to use wireless internet or ethernet, and, wanting more stability and a faster connection, I chose ethernet, and it worked fine, and still does.

However, I noticed that I no longer see any wireless networks in my network dropdown.  When I got my card working I needed to add a MAC address manually to a config file; I checked and it was still there, so I am not sure what has changed.

I have been booting and shutting down and Suspending with the cable still inside the laptop - I think this has something to do with it.  Does anyone know whether this can affect my scenario and, if so, how I can re enable wireless usage on my machine?

---

### Post by dai_vernon on 2008-09-26
I hate to bamp, but this is important.  So...

Bamp.  Can anyone at least direct me to some help?

---

### Post by Crafty Kisses on 2008-09-26
Post the results of this command:
```
ifconfig
```

---

### Post by dai_vernon on 2008-09-26
```
eth0      Link encap:Ethernet  HWaddr 00:1e:68:61:46:69  
          inet addr:128.175.65.8  Bcast:128.175.65.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe61:4669/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1861453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:191035 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:421324003 (401.8 MB)  TX bytes:54345416 (51.8 MB)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4900 (4.7 KB)  TX bytes:4900 (4.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:1c:3d:60  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f6000000-f6010000 
```

---

### Post by superprash2003 on 2008-09-26
please post output of iwconfig

---

### Post by dai_vernon on 2008-09-28
Sorry for the late reply.  Tests, etc.  Here's iwconfig:```


lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by superprash2003 on 2008-09-29
i think its a drivers issue, type lshw -C network in the terminal and post output

---

### Post by dai_vernon on 2008-09-29
```
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1e:68:61:46:69
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=DERP latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:e1:1c:3d:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net5211 driverversion=1.52+,06/21/2007,5.3.0.56 latency=0 link=no module=ndiswrapper multicast=yes wireless=IEEE 802.11b
```

---

### Post by superprash2003 on 2008-09-30
[http://ubuntuforums.org/showthread.php?t=766169](http://ubuntuforums.org/showthread.php?t=766169)

---

