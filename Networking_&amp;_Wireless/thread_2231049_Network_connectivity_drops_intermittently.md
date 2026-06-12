---
title: "Network connectivity drops intermittently"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by Robbie_68 on 2014-06-23
I am running a dual boot configuration with Ubuntu 14.04 and Windows 7. It works great for the most part, but occasionally the wired ethernet network access drops in Ubuntu for any site beyond the local network. The Ethernet connection itself remains connected but cannot access any website or cannot ping to yahoo or gmail for instance. Rebooting Ubuntu doesn't help. But when start Windows 7, things are normal and then when I reboot Ubuntu the full connectivity is restored. I have no clue what is happening.

System: Intel® Core&#8482;2 Duo CPU P8600 @ 2.40GHz × 2 
Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)

My ifconfig output is below:  

```
eth0      Link encap:Ethernet  HWaddr 00:24:e8:c7:34:3a  
          inet6 addr: 2001:cc0:b004:151:ed0d:d0d1:f57d:64bb/64 Scope:Global
          inet6 addr: fe80::224:e8ff:fec7:343a/64 Scope:Link
          inet6 addr: 2001:cc0:b004:151:224:e8ff:fec7:343a/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2714 errors:0 dropped:65 overruns:0 frame:0
          TX packets:119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:251590 (251.5 KB)  TX bytes:24797 (24.7 KB)
          Interrupt:22 Memory:f6ae0000-f6b00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:578 errors:0 dropped:0 overruns:0 frame:0
          TX packets:578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53472 (53.4 KB)  TX bytes:53472 (53.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:b5:eb:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I'd appreciate any pointers on this.

Thank you,
Robert

---

### Post by Bucky Ball on 2014-06-23
*Thread moved to **Networking & Wireless**.*

You may have more luck here and, as you've just arrived, helpers will be gentle. ;)

I can't help with your problem, but can provide a tip: please use ```
 tags [ /code] around terminal output. Holds the format, clearer and easier to read. I have inserted them in your last post as an example. Cheers and good luck.

PS: Could you also provide the output of:
[code]
sudo lshw -C network
```

Thanks.

---

