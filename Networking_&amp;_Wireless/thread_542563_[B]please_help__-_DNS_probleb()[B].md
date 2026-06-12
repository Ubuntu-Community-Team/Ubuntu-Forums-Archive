---
title: "[B]please help  - DNS probleb(?)[/B]"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by mooli on 2007-09-04
hello
I have installed on my PC both ubuntu && winxp op - (using wubi).
My Internet connection (trough a router with a network cable) works fine under windows.in ubuntu there is a problem.
The reason i think it's a dns problem is because when i type the in the url 82.211.81.186 i get to the ubunto forums.

when i type in the console if config i get this:

Quote:
eth0 Link encap:Ethernet HWaddr 00:16:76:A0:5F:F1 
inet addr:192.168.0.106 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::216:76ff:fea0:5ff1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:402 (402.0 b) TX bytes:4493 (4.3 KiB)

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)

Link encap:Ethernet HWaddr 00:16:76:A0:5F:F1 
inet addr:192.168.0.106 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::216:76ff:fea0:5ff1/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:402 (402.0 b) TX bytes:4493 (4.3 KiB)

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:2 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:100 (100.0 b) TX bytes:100 (100.0 b)  

and when i type lspci i get this:

Quote:
00:00.0 Host bridge: Intel Corporation 82946GZ/PL/GL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82946GZ/GL Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
04:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 01)  

Whats my problem and how do i fix it?
please help...

---

### Post by noob12 on 2007-09-04
OK.  Sounds like things are almost working for you.  

The output from these would be helpful for diagnosis in this case
```

cat /etc/network/interfaces

cat /etc/resolv.conf

```

You might try manually setting your nameservers to the free OpenDNS servers to see if that helps:
208.67.222.222 
208.67.220.220

You can do this in the System | Administration | Network | DNS tab.  Replace the server you have with these and see if it helps.

---

### Post by mooli on 2007-09-04
I guess things WERE almost working for me.

The OpenDNS servers worked like a charm,
and i'am now working under ubuntu. 

THANK'S A LOT NOOB12.

---

### Post by noob12 on 2007-09-04
Great.   If you find that your settings keep getting overwritten by DHCP.  You may want to configure those in your router.

---

