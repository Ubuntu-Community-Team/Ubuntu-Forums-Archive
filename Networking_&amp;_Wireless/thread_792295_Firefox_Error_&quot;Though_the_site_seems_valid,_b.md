---
title: "Firefox Error: &quot;Though the site seems valid, but...&quot;"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by elint6 on 2008-05-12
I just got Ubuntu installed for the first time, and my wired ethernet is working fine. My wireless, on the other hand, not so much. Wifi-radar and iwlist scan picks up wireless networks fine (but lists them as B instead of G, but whatever).

However, connecting them via wifi radar, I get "IP not obtained." I have entered the proper 64-bit WEP key as hexidecmial, etc, etc. 

Netapplet does not work either.

When I try to connect to my router directly via 192.168.1.1 in firefox, I get a peculiar error: "Firefox can't establish a connection to the server at 192.168.1.1...Though the site seems valid, the browswer was unable to establish a connection."

From lspci: 
0c:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

I installed the driver through synaptic: b43-fwcutter version 1:011-1 (latest version)

My router is Verizon Fios MI424WR. 

Thanks!

---

### Post by superprash2003 on 2008-05-12
go to system->administration->network and go to wireless card properties.. and select DHCP .. if you still dont get an ip .. try entering ip address manually.. also please post your iwconfig and ifconfig output

---

### Post by elint6 on 2008-05-12
I tried the System->Admin method. I still cannot access any website, and the 192.168.1.1 comes up with the same error.

**My IWCONFIG:**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"MBAP2"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:01:EF:14:82   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=60/100  Signal level=-73 dBm  Noise level=-67 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**MY IFCONFIG:**

eth0      Link encap:Ethernet  HWaddr 00:14:22:a9:c4:bb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:214841 errors:3 dropped:1 overruns:0 frame:0
          TX packets:86597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:172389135 (164.4 MB)  TX bytes:10766748 (10.2 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79794 (77.9 KB)  TX bytes:79794 (77.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:16:ce:6a:2f:94  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16138 (15.7 KB)  TX bytes:5928 (5.7 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:16:ce:6a:2f:94  
          inet addr:169.254.6.145  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-16-CE-6A-2F-94-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Manual IP pulling does not work either.

---

### Post by superprash2003 on 2008-05-13
ensure that your router has DHCP enabled!!the problem is you arent getting an ip when you should!!

---

