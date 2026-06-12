---
title: "Intel Pro 3845ABG not recognized dell xps m1210"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by nymphaeles on 2006-10-20
In a Dell xps m1210 laptop, wireless card 3945abg isn't recognized.  Any suggestions? Here are some info on lspci and ifconfig, iwconfig

```

lspci
0000:0c:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)
        Subsystem: Intel Corporation: Unknown device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at dcfff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable -
        Capabilities: [e0] #10 [0011]
```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:3E:BE:D0
          inet addr:192.168.72.61  Bcast:192.168.72.255  Mask:255.255.255.0
          inet6 addr: fe80::215:c5ff:fe3e:bed0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5790 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2748033 (2.6 MiB)  TX bytes:522715 (510.4 KiB)
          Interrupt:177

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:572 (572.0 b)  TX bytes:572 (572.0 b)
```


```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by nymphaeles on 2006-10-20
no ubuntu diehards wans to take a challenge?

---

### Post by brsseb on 2006-10-27
[http://wiki.gacq.com/index.php/Installing_Debian_on_Dell_M1210](http://wiki.gacq.com/index.php/Installing_Debian_on_Dell_M1210)
See wireless section

---

### Post by abarth on 2006-11-25
Which version of Ubuntu are you using?

According to the supported Hardware list your card should work "out of the box", at least on Ubuntu 6.06.
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported")

I bought also a Dell XPS M1210. I will have it next week.

Alex

---

### Post by BennyHustle on 2006-12-02
Well, it works but it doesn't support wep or wpa encryption, which doesn't really help that much. 

I've tried following the instructions on that site for both 6.06 and 6.10, and I still get all kinds of error messages when I try to do a make file for the driver. 

Is there anybody who's gotten WEP or WPA working on this?

---

### Post by brsseb on 2006-12-02
Im using WPA on my home wireless LAN, and it works without problems on my m1210 with Ubuntu 6.06. The wireless router is currently set up to use WPA with AES chiper. Havent tried other chipers like TKIP or AES & TKIP combined.

---

### Post by Alfdog on 2007-03-12
I had this same problem, but if you search for 3945, you'll find the easy solution, which is to install "network manager"

---

