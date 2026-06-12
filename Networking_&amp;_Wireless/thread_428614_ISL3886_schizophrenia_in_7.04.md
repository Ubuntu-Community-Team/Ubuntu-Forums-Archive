---
title: "ISL3886 schizophrenia in 7.04"
date: 2007-04-30
forum: Networking &amp; Wireless
---

### Post by Jabithew on 2007-04-30
I have a generic wireless PCI card which uses the Intersil ISL3886 chipset. Here's how it looks according to lspci
```
Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
03:08.0
```

I found some windows drivers and added them into ndiswrapper on the command line. 

The bizarre thing is that the hardware information screen (from the GUI) shows the card as being of unknown use. It also doesn't show up in the Network Manager or the ndisgtk interface, even though the latter shows the driver. Yet:
```

jabithew@RGALLEN:~$ ndiswrapper -l
wlancig : driver installed
        device (1260:3886) present
```

I can see a lot of people having problems with the chipset, but haven't found a problem/solution the same as mine. Can anyone suggest a way to tell Ubuntu that the car is a network interface/is there?

P.S. Whoops, here's some vitals : I'm running Ubuntu 7.04 64-bit on a dual boot with Windows XP. Everything else seems to be working fine, aside from the fact that I have an ATI X1600 graphics chip.

---

### Post by knoest on 2007-05-01
Exactly the same problem here; now with the 386 version of Feisty. The card is a sitecom WL-141, although it's found by Ubuntu, it is not recognized as a wifi device, so installing the windows drivers in ndiswrapper gives no help.

Any one please?

An Ubuntu newbee

Knoest

---

### Post by Jabithew on 2007-05-11
Ok, additional information, output from ifconfig and iwconfig. Nothing particularly eye-opening here.

```
jabithew@RGALLEN:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3F:9B:B3:D1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth0:avah Link encap:Ethernet  HWaddr 00:12:3F:9B:B3:D1  
          inet addr:169.254.9.67  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:624 (624.0 b)  TX bytes:624 (624.0 b)

jabithew@RGALLEN:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by the review site on 2007-09-03
I have the same problem. has anybody managed to get this working?

Many Thanks

Lee

---

