---
title: "More wireless problems"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by bluedruid on 2010-05-04
I clean installed 10.04 after I had 9.10 a my laptop. I am having the same problem with both installs. I can connect to networks but can not get anything from the internet. It seams to be going extremely slow. My laptop burned out the wireless card when I had windows on it so I am running a Belkin USB card for wireless internet. I can connect with ethernet just fine. I did the clean install of 10.04 because I went from 32 bit to 64 bit. I love Ubuntu but would really like to get the wireless to work. Thank you

---

### Post by xumuk37 on 2010-05-04
```
lspci|grep -i wireless
ifconfig 
lsmod|grep 802
```post the outputs in pastebin.com or right here

---

### Post by bluedruid on 2010-05-04
Heres what came up:


-laptop:~$ lspci|grep -i wireless
tom@tom-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 76:db:28:d2:95:5a  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::74db:28ff:fed2:955a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:932 errors:0 dropped:0 overruns:0 frame:0
          TX packets:803 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:942024 (942.0 KB)  TX bytes:112289 (112.2 KB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8400 (8.4 KB)  TX bytes:8400 (8.4 KB)

tom@tom-laptop:~$ lsmod|grep 802
tom@tom

---

