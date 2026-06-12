---
title: "Problem with Intel PRO/wireless 3945ABG connection"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by ruud08 on 2008-10-15
Hi,

I have a strange problem with my Intel PRO/wireless 3945ABG conection. When I start Ubuntu 8.04 (Hardy Heron) the wireless network connection works perfectly for 5-10 minutes and then it disconnect from the internet. Sometimes it works for a while when I only browse the internet but when I update the Ubuntu system or download files from the newsgroups, the internet disconnect. 

After this I move my mouse over the wireless icon at the upper right toolbar and it show "Wireless network connected with [routername] (90%)". But from the terminal 'ping 192.168.1.13' I get an error, no packets received, there is no connection. Below you see some output during a short working connection.

I use Ubuntu 8.04.1 with Kernel version 2.6.24-19 installed. The driver installed is 'iwl3945'. In an previous installation, NDISWRAPPER cause an system crash with an IRQ interupt problem so this is a new installation of Ubuntu.

Can someone help me with this?

Thanks, Ruud08

ruud@Acer5610Linux:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d4:aa:2f:2d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:18:de:c9:14:d1  
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:deff:fec9:14d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:138856 (135.6 KB)  TX bytes:30569 (29.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82500 (80.5 KB)  TX bytes:82500 (80.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-C9-14-D1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


ruud@Acer5610Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11g  ESSID:"Livebox-761b"  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:21:86:3F:CF:E8   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
          Power Management:off
          Link Quality=87/100  Signal level=-46 dBm  Noise level=-76 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

