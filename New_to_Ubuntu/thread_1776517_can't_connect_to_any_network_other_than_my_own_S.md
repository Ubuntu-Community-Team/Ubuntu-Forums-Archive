---
title: "can't connect to any network other than my own? :S"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by CaptainSnowman on 2011-06-06
So I've been using ubuntu on my laptop for about a month now and it has been brilliant however it will not connect to any network other than my own. Can anyone help me?
 
I'm using version 10.04 LTS 32-bit and my laptop is a Dell Latitude D610. The router I am trying to connect to at the moment is a sky router.

---

### Post by Peter09 on 2011-06-06
can you provide the output of the command

```
route
```

---

### Post by CaptainSnowman on 2011-06-06
The output is:
 
Kernel IP routing table
Destination     Gateway    Genmask    Flags Metric Ref    Use Iface

---

### Post by Peter09 on 2011-06-06
please do 

```
ifconfig
```

---

### Post by CaptainSnowman on 2011-06-06
Output:
 
eth0 - Link encap:Ethernet Hwaddr 00:12:3f:0a:3c:70
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 frame:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 
eth1 - Link encap:Ethernet HWaddr 00:13:ce:10:dc:75
inet6 addr: fe80::213:ceff:fe10:dc75/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX Packets:80 errors:80 dropped:88 overruns:0 frame:0
TX packets:80 errors:0 dropped:5 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:9040 (9.0 KB) TX bytes:10433 (10.4 KB)
Interrupt:17 Base address:0x8000 Memory:dfbff000-dfbfffff
 
lo - Link encap:Local loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
inet6 addr::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 frame:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

---

### Post by Peter09 on 2011-06-06
OK - lets see whats in you system logs for eth1, can you post the output of

```
dmesg | grep eth1
```

---

### Post by Peter09 on 2011-06-06
Just to confirm, you are trying to connect using a wired link, not wireless.

---

### Post by Peter09 on 2011-06-06
note command should be dmesg

---

