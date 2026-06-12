---
title: "Slow Network Performance in 8.10"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by Infinitas on 2008-11-19
I recently upgraded to Ubuntu 8.10 from 8.04 and am having some weird networking issues. When transferring data the transfer seems to be limited to 1.5 MBps. This happens when I am trying to use my 802.11g wireless or my gigabit wired NIC. I have noticed, however, that if I start multiple transfers, they will go at 1.5 MBps each until I reach the limits of the NIC. Any thoughts on this?

-Infinitas

---

### Post by jonobr on 2008-11-19
Could you post the results of ifconfig 
Having a gig nic and 1.5 is criminal:-)

---

### Post by Infinitas on 2008-11-19
I'm actually in the middle of a large transfer right now. I'm on my wireless and my ethernet isn't hooked up (as you can tell from the commands below).

```


[~]
asmith@lappy: ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:86:21:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fe200000-fe220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20356 (20.3 KB)  TX bytes:20356 (20.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:ba:dd:f2  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:feba:ddf2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1429790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:830345 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2043313000 (2.0 GB)  TX bytes:80622449 (80.6 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-BA-DD-F2-64-66-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

[~]
asmith@lappy: iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Infinitas"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:EE:A8:51   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=92/100  Signal level:-48 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by jonobr on 2008-11-20
Yep

I wanted to check your MTU and that looks ok,

You should search for IPV6 posts,
theres mention that having both enabled slows down the IPV4 experience

---

