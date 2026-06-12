---
title: "Ubuntu 7.10 Atheros 5700EG (Almost working but one prob.)"
date: 2008-04-19
forum: Networking &amp; Wireless
---

### Post by David26 on 2008-04-19
Hello, I posted before, and I finally got my Atheros card being regonized by Ubuntu 7.10 64 Bit with ndiswrapper and acer_acpi and 64bit Windows XP Drivers. Anyway, I can see all Wireless Networks, but I still have problems with connecting to them. When I insert the network key wich is WPA, it says connected, but I am ain't. I need help. Thank you.

iwconfig
```
wlan0     IEEE 802.11g  ESSID:"Livebox-d26d"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

ifconfig
```
wlan0     Link encap:Ethernet  HWaddr 00:19:7E:69:DD:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2988 (2.9 KB)  TX bytes:4666 (4.5 KB)
          Interrupt:17 Memory:c0200000-c0210000
```

---

### Post by David26 on 2008-04-20
Hello does anyone hears me :S:confused::confused::confused::confused::confused::confused:

---

### Post by virtualsid on 2008-04-25
I'm not able to help - but I'm hoping you could help me - where did you find the ndis driver for this card? I have a Toshiba laptop with the same card, but I'm not having much luck with ndis drivers - probably because I've no clue how it works - every driver I try to add (from the Windows Vista partition) says 'invalid driver' or somesuch.

If I can get to your level of working, I might be able to tell you what I can see too...

Thanks,

Sid

---

