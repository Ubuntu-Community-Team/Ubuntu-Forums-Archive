---
title: "wireless problem after upgrade"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by aam-aadmi on 2010-05-09
Hi All,

I am using a HP dv2500 machine and upgraded to Ubuntu 10.04 LTS right now. After the upgrade I am facing wireless problems: when I start the machine and Ubuntu boots up the wireless is working. Within a few minutes the wireless gets disconnected and then I am not able to connect up again. If I re-start the computer at this point the wireless starts working after the re-start. But after a few minutes it is disconnected again.

Any help will be appreciated.

Aam-aadmi

---

### Post by aam-aadmi on 2010-05-09
Here is some information that might help in solving the problem.

ifconfig

[HTML]eth0      Link encap:Ethernet  HWaddr 00:1d:72:41:18:4f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:61:04:f4  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe61:4f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25390 (25.3 KB)  TX bytes:10563 (10.5 KB)
[/HTML]

iwconfig
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Deepriyanka"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:A9:04:8F   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/HTML]

Thanks in advance.

---

### Post by Sealbhach on 2010-05-09
That's a little strange. If I were you, I would install wicd, and see if the same thing happens when you use wicd as your network manager.

.

---

### Post by aam-aadmi on 2010-05-09
I realized that the problem is related to Mozilla Thunderbid (the e-mail client). Once when I re-started the machine and did not open Thunderbird the wireless was working fine; when I opened Thunderbird the wireless was down within a few minutes.

Did anyone face asimilar problem?

Aam-aadmi

---

