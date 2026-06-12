---
title: "Wireless Quit Working -- Please Help"
date: 2006-09-24
forum: Networking &amp; Wireless
---

### Post by onioneater36 on 2006-09-24
I had my wireless working, but it stopped.  I have a Netgear WG511T card (atheros chipset).  Here is some are the results of the checking I did...

I type "iwconfig"...  I get...

```
ath0      IEEE 802.11g  ESSID:"??? blocked for security ???"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:10:F9:77
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/94  Signal level=-44 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:1   Missed beacon:3
```

I type "ifconfig"...  I get...

```
ath0      Link encap:Ethernet  HWaddr 00:0F:B5:23:BD:15
          inet6 addr: fe80::20f:b5ff:fe23:bd15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1528 errors:4 dropped:0 overruns:0 frame:4
          TX packets:48 errors:1 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200
          RX bytes:78155 (76.3 KiB)  TX bytes:8280 (8.0 KiB)
          Interrupt:11 Memory:e0b40000-e0b50000

eth0      Link encap:Ethernet  HWaddr 00:08:74:3F:13:20
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::208:74ff:fe3f:1320/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:34580 (33.7 KiB)  TX bytes:5334 (5.2 KiB)
          Interrupt:11 Base address:0xcc00
```

I originally used network-manager-gnome, but removed it and tried the ndiswrapper method.  From the results of my "iwconfig" shown above, it almost looks like I am successfully authenticating with my Access Point as I can see the correct MAC address of my AP.

Also, my wireless NIC has 2 leds that flash in unison.  This usually means everything is working (which I think explains the results of iwconfig), yet I am not receiving an IP.  Using a static IP didn't work either.

In the "ifconfig" results, however, you can see that my ath0 interface is not receiving an IP4 IP address.  I am sure this is the problem but I don't know how to correct it.  Any way to blow away ALL wireless networking putzing and start over?  Or better yet, do you know my problem and have a suggestion for how to proceed?

Thanks in advance...

---

### Post by onioneater36 on 2006-09-25
Hello...  Hello... Hello....


Is there anybody out there.....

                         --Pink Floyd

---

### Post by NetworkGuy on 2006-09-25
what happens when you try ```
sudo dhclient ath0
```

---

### Post by onioneater36 on 2006-09-25
Thanks for the reply, NetworkGuy...  Judging by your name, I would have to bet I have an expert on this subject.  Anyway...  Here is what I get after executing your command...

```
onioneater36@onioneater36-lappy:~$ sudo dhclient ath0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/ath0/00:0f:b5:23:bd:15
Sending on   LPF/ath0/00:0f:b5:23:bd:15
Sending on   Socket/fallback
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPREQUEST on ath0 to 255.255.255.255 port 67
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
Trying recorded lease 192.168.1.4
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

```

Hope this helps...  I am trying my best not to just reinstall.  I have got to learn how to figure these things out and learn more about Linux.  Ubuntu is really re-invogorating my drive to convert.  I have it on my lappy and on an old P3-500Mhz downstairs (and it runs AWESOME on that old junker).  Dare I try it on a P1-100MHz?  Naw.

Thanks again for the assistance.

---

### Post by jakejas on 2007-08-30
I am also having a similar problem. I had my wireless card working perfectly, and then it quit.

Here is the results of some stuff I typed in the command window:

jakejas@jakejas-laptop:~$ iwconfig 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318" 
          Mode:Managed  Access Point: Invalid    
          RTS thr:off   Fragment thr:off 
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
jakejas@jakejas-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:08:02:D4:F4:AB   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:84684 (82.6 KiB)  TX bytes:8563 (8.3 KiB) 
 
eth0:avah Link encap:Ethernet  HWaddr 00:08:02:D4:F4:AB   
          inet addr:169.254.9.176  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:1146 (1.1 KiB)  TX bytes:1146 (1.1 KiB) 
 
jakejas@jakejas-laptop:~$ sudo dhclient athO 
Password: 
Internet Systems Consortium DHCP Client V3.0.4 
Copyright 2004-2006 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/) 
 
SIOCSIFADDR: No such device 
athO: ERROR while getting interface flags: No such device 
athO: ERROR while getting interface flags: No such device 
Bind socket to interface: No such device 



If anyone could help me with this, I would appreciate it.

---

