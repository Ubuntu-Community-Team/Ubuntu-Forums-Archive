---
title: "Nmap tool extremely slow"
date: 2016-03-11
forum: Networking &amp; Wireless
---

### Post by Hyne on 2016-03-11
Hi all, I've got this big problem using nmap in my laptop, it runs extremely slow, a normal scan takes normaly more than 10/15 minutes, I'm experiencing this issue since the first time I installed nmap on Windows.
 I recently installed Ubuntu but this problem persist, I think that is casued by the Wi-Fi card because if I try to run the same nmap scan inside a virtual machine it executes perfectly in less than 10 seconds.
 Here are my specs:

 Laptop:          Acer Aspire E5-571G-71E7
 OS:               Ubuntu 15.10 64-Bit (No Dual boot, only ubuntu installed)
 RAM:                8 GB DDR3
 CPU:             Intel Core i7-4510U 2.0GHz
 Wi-Fi Card:    Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter

 Output running lspci -v:
```
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. QCA9565 / AR9565 Wireless Network Adapter
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at b3400000 (64-bit, non-prefetchable) [size=512K]
    Expansion ROM at b3480000 [disabled] [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/4 Maskable+ 64bit+
    Capabilities: [70] Express Endpoint, MSI 00
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [140] Virtual Channel
    Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00
    Kernel driver in use: ath9k
    Kernel modules: ath9k
```

Output running iwconfig:
```
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TeleTu_DC0B1A0C599E"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: DC:0B:1A:0C:59:9E   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

lo        no wireless extensions.
```

Output running route -n:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0
```

I use this nmap command:
```
nmap scanme.nmap.org
```
If I try to use it with -T4/-T5 flags nothing change, it still takes at least 10 minutes to complete the scan.

Hope that someone knows how to fix this problem.
Thank you.

---

### Post by TheFu on 2016-03-11
nmap requires elevated permissions to work.

Found this [https://nmap.org/book/man-performance.html](https://nmap.org/book/man-performance.html) which might help.

**sudo nmap -sT 1.2.3.0/24** is my normal command.  If pings aren't being returned, then a -P0 option is needed to prevent ping tests first.  This is all spelled out in the nmap manpage. 

Since you are scanning a network you control, double-check that the network devices aren't slowing down the scan as a good IDS/IPS should.

---

