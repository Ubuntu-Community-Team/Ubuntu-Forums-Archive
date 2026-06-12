---
title: "Wireless help on a LAMP Server"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2006-09-14
I am so lost and a newbie - any help would be greatly appreciated.

I have a D-link DWL-G510 Version B on a Pentium III Gateway.  I used the install disk, but it didn't recognize the card.  I have read so many different threads, have installed ndiswrapper, downloaded RT61 RALink Linux drivers, updated the /etc/network/interfaces file to include ra0, etc - 

I'm including some of the outputs I have seen others post

First lspci

```
lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:02.0 VGA compatible controller: Intel Corporation 82815 CGC [Chipset Graphics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 02)
```

Next ifconfig
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

Any help greatly appreciated

---

