---
title: "Cannot resolve hosts periodically"
date: 2017-05-31
forum: Networking &amp; Wireless
---

### Post by sorush on 2017-05-31
Hi guys. I'm using ubuntu 16.04 and everything was working perfectly until I ran sudo apt upgrade.
Now I'm facing with many network errors.

Here it is my uname -a:

```

Linux soroush-system 4.8.0-53-generic #56~16.04.1-Ubuntu SMP Tue May 16 01:18:56 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

And here it is my ifconfig output:
```

docker0   Link encap:Ethernet  HWaddr 02:42:ea:89:75:d5  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp0s31f6 Link encap:Ethernet  HWaddr 34:97:f6:da:ec:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:df300000-df320000 


enp5s0    Link encap:Ethernet  HWaddr f4:f2:6d:04:de:65  
          inet addr:192.168.99.148  Bcast:192.168.99.255  Mask:255.255.255.0
          inet6 addr: fe80::d1e7:d168:d2d:f196/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7523 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7294 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4532163 (4.5 MB)  TX bytes:1259850 (1.2 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:125774 (125.7 KB)  TX bytes:125774 (125.7 KB)

```

I can use internet for max 5 mins and after that I should run sudo service network-manager restart to be able to resolove hosts again ....

---

### Post by username2758 on 2017-05-31
I'm also using 16.04 and not sure if it's related but after upgrading the system have been experiencing problems with Samba not starting up correctly. I'm not an expert in Linux so hoping that someone might help me with this!

 [https://ubuntuforums.org/showthread.php?t=2362586](https://ubuntuforums.org/showthread.php?t=2362586)

---

