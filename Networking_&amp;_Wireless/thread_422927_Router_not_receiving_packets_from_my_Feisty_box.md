---
title: "Router not receiving packets from my Feisty box"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by dmhouse on 2007-04-25
Hey all,

I've recently installed Feisty on my laptop, and I'm having real trouble getting the wireless to work. After much digging, I think the problem is that the router isn't receiving any of the packets I'm sending. Specifically, looking at the 'Traffic Stats' area of my router configuration, the RX packet count doesn't change whilst pinging the router.

Some details: my wireless card is on eth1. My router is at 192.168.1.1 and my laptop has a static IP of 192.168.1.90. Here's the result from ifconfig, iwconfig, arp and route:

```
david@tarn:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:D3:00:00:08  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x4400

eth1      Link encap:Ethernet  HWaddr 00:15:00:4D:D1:9D  
          inet addr:192.168.1.90  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:ff:fe4d:d19d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:298 errors:81 dropped:81 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:4759 (4.6 KiB)
          Interrupt:18 Memory:b0106000-b0106fff

eth0:avah Link encap:Ethernet  HWaddr 00:16:D3:00:00:08  
          inet addr:169.254.1.229  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 Base address:0x4400

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1614 (1.5 KiB)  TX bytes:1614 (1.5 KiB)

david@tarn:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"pizza"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 00:90:96:FB:BB:5F   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=89/100  Signal level=-40 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:82  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

david@tarn:~$ route
Kernel IP routeing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
default         *               0.0.0.0         U     1000   0        0 eth0
david@tarn:~$ arp -n
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1                      (incomplete)                              eth1
```

Naturally ARP isn't working because the router isn't seeing my arp who-has broadcasts. I can manually add the entry to the ARP table:

```
david@tarn:~$ sudo arp -s 192.168.1.1 00:11:F5:12:9F:AA
```

Then ping just sits there sending out packets. Using tcpdump I can watch them leave, but, as mentioned, the RX packet count doesn't increment in the router stats page.

Any suggestions?

---

### Post by dmhouse on 2007-04-26
Rereading the above, it does sound like my laptop isn't getting connected to the network whatsoever! However, I don't think this is the case; my MAC address appears in 'Wireless Clients' section of my router configuration, so the router must at least be recieving some packets.

Some hardware details: I have a BT Voyager 2100 Wireless ADSL router and an 'Intel Corporation PRO/Wireless 2200BG Network Connection'.

Anyone got any ideas? Much appreciated.

---

