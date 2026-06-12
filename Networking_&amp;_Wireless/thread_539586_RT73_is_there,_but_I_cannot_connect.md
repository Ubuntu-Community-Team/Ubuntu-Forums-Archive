---
title: "RT73 is there, but I cannot connect"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by Spanglish on 2007-08-31
Hi,

I am trying to get a Belkin USB wireless (rt73) going on an old compaq presario 2500, with Xubuntu 7.04 installed. I have followed all the instructions on [http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)

The hardware seems to be working, but I cannot get an IP from my access point (which is configured for WPA-PSK). I have been at this for a few days now, and I only seem to be going round in circles! This is what I have at the moment:

*** Output for iwlist scan:

wlan1     Scan completed :
          Cell 01 - Address: 00:02:CF:50:31:C5
                    ESSID:"WLAN_1C"
                    Mode:Managed
                    Channel:4
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:01:38:71:ED:70
                    ESSID:"WLAN7C"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 03 - Address: 00:01:38:68:A9:3E
                    ESSID:"WLAN_01"
                    Mode:Managed
                    Channel:6
                    Encryption key:on
                    Bit Rates:0 kb/s

WLAN7C is my own access point...  

***For ifconfig (note that my cable connection is in place at the moment, but I have also tried without it):

eth0      Link encap:Ethernet  HWaddr 00:0B:CD:8A:0F:94  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe8a:f94/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:33718 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37121747 (35.4 MiB)  TX bytes:3658971 (3.4 MiB)
          Interrupt:10 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41352 (40.3 KiB)  TX bytes:41352 (40.3 KiB)

wlan1     Link encap:Ethernet  HWaddr 00:17:3F:13:F8:6B  
          inet6 addr: fe80::217:3fff:fe13:f86b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:50500 errors:0 dropped:8 overruns:8 frame:8
          TX packets:69388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5656700 (5.3 MiB)  TX bytes:4996224 (4.7 MiB)

wlan1:ava Link encap:Ethernet  HWaddr 00:17:3F:13:F8:6B  
          inet addr:169.254.6.198  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

Any more info needed? Thanks.

---

