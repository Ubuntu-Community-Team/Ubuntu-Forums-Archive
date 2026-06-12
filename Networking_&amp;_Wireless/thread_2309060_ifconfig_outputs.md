---
title: "ifconfig outputs"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by monkeybrain20122 on 2016-01-07
Hi, 

When I run ifconfig on Ubuntu 15.10 I get
```
enp11s0   Link encap:Ethernet  HWaddr 78:2b:cb:ce:1d:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:120802 (120.8 KB)  TX bytes:120802 (120.8 KB)

wlp2s0b1  Link encap:Ethernet  HWaddr 68:a3:c4:2f:07:b0  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe2f:7b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3080782 (3.0 MB)  TX bytes:377587 (377.5 KB)

```

But on Ubuntu 15.04 on the same machine
```
eth0      Link encap:Ethernet  HWaddr 78:2b:cb:ce:1d:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:382 errors:0 dropped:0 overruns:0 frame:0
          TX packets:382 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84203 (84.2 KB)  TX bytes:84203 (84.2 KB)

wlan0     Link encap:Ethernet  HWaddr 68:a3:c4:2f:07:b0  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6aa3:c4ff:fe2f:7b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:242 errors:0 dropped:0 overruns:0 frame:0
          TX packets:256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:253320 (253.3 KB)  TX bytes:29623 (29.6 KB)


```

So the names eth0 and wlan0  have changed to enp11s0 and wlp2s0b1? What happened?

---

### Post by chili555 on 2016-01-07
Please see: [http://askubuntu.com/questions/704361/why-is-my-network-interface-named-enp0s25-instead-of-eth0](http://askubuntu.com/questions/704361/why-is-my-network-interface-named-enp0s25-instead-of-eth0)

Welcome to the future!

---

### Post by monkeybrain20122 on 2016-01-10
Thanks for the explanation.

---

