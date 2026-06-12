---
title: "Ethernet not detected and eth0 not found"
date: 2016-06-23
forum: Networking &amp; Wireless
---

### Post by chakvs on 2016-06-23
Hi ! 

I am new to ubuntu. The ethernet got detected until today, and I could use internet for only one minute or so. Then, even tough is shows connected at the top corner, it doesn't connect. I have searched some forums, and completely made a mess of everything. 
Now, I do not find eth0, ethernet does not even show up. I need someone to help me. 
Thank you.

Some of the output for some common codes:

$ ifconfig
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:742 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:404013 (404.0 KB)  TX bytes:404013 (404.0 KB)

wlan0     Link encap:Ethernet  HWaddr 60:d8:19:9f:60:d5  
          inet addr:10.136.100.140  Bcast:10.136.127.255  Mask:255.255.128.0
          inet6 addr: fe80::62d8:19ff:fe9f:60d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8070 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9511026 (9.5 MB)  TX bytes:1157575 (1.1 MB)
```

$ sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 01
       serial: 60:d8:19:9f:60:d5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.19.0-61-generic firmware=N/A ip=10.136.100.140 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f7a00000-f7a0ffff
```

$ lspci```

.....................................
.....................................
09:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0b:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
```

$ ethtool eth0
```

0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available
```

$ cat /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

#primary network interface

auto eth0
iface eth0 inet dhcp
```

---

### Post by HereInOz on 2016-06-24
My guess would be that either you have inadvertently disabled the ethernet adaptor in the BIOS, or you have had a failure of the ethernet adaptor.  If lspci is not seeing it, then it is either turned off or it has failed.

I can think of no other possibilities.

---

### Post by jeremy31 on 2016-06-24
Moved to Networking

---

### Post by QIII on 2016-06-24
@chakvs:

Rather than using PHP tags, please use code tags.

You can do that by:

1.  Clicking the # symbol in the toolbar above the text entry box, placing your cursor between the tags and pasting your text.

2.  Highlighting text already present and clicking the # symbol in the toolbar.

3.  Typing [noparse]```
[/noparse] before the text and [noparse]
```[/noparse] after the text.  The square brackets are required.

---

