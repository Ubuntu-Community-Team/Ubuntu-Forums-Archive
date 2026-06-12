---
title: "Help with wireless network connection"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by knowledene on 2008-11-30
Hi... I'm failing to get a network connection using an Intel PRO/Wireless 2200BG card on a Dell Inspiron 630m with Ubuntu 8.04. As far as I can see, I'm connecting ok to the router, but getting no data transfers.  After Googling, I found that Ipv6 was enabled, so disabled it by aliasing net-pf-10 to off.
Can someone please advise? 

iwconfig gives :- 

 terry@dell-linux:~$ iwconfig  

lo        no wireless extensions. 

eth0      no wireless extensions. 


eth1      IEEE 802.11g  ESSID:"FRITZ!Box Fon WLAN 7140 Annex A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:4A:4B:BA:E0   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/100  Signal level=-55 dBm  Noise level=-89 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

ifconfig gives :- 

eth0      Link encap:Ethernet  HWaddr 00:14:22:99:b0:a9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:43:05:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:7458 (7.2 KB)  TX bytes:12068 (11.7 KB) 
          Interrupt:17 Base address:0x4000 Memory:dfbfd000-dfbfdfff 

eth1:avahi Link encap:Ethernet  HWaddr 00:16:6f:43:05:fd  
          inet addr:169.254.6.195  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:17 Base address:0x4000 Memory:dfbfd000-dfbfdfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:3584 (3.5 KB)  TX bytes:3584 (3.5 KB) 

lspci gives :- 

02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

---

