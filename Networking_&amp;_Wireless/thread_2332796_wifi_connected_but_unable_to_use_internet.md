---
title: "wifi connected but unable to use internet"
date: 2016-08-04
forum: Networking &amp; Wireless
---

### Post by bestpain on 2016-08-04
i am able to connect to my wifi but there is no internet access.
and i am totally new to ubuntu.
here are some results 
```
lspci -nnk | grep -iA2 net02:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n [17aa:0611]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros QCA8172 Fast Ethernet [1969:10a0] (rev 10)
    Subsystem: Lenovo QCA8172 Fast Ethernet [17aa:3801]
    Kernel driver in use: alx
    Kernel modules: alx

bestpain@bestpain-Lenovo-G510:~$ ifconfig
enp0s20u2 Link encap:Ethernet  HWaddr 02:68:6c:79:74:04  
          inet addr:192.168.42.98  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::4449:b86b:2e69:c82b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72814 errors:1 dropped:0 overruns:0 frame:1
          TX packets:65574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77092214 (77.0 MB)  TX bytes:9412753 (9.4 MB)

enp3s0    Link encap:Ethernet  HWaddr 20:89:84:f5:34:5a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:9798 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9798 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1092615 (1.0 MB)  TX bytes:1092615 (1.0 MB)

wlp2s0    Link encap:Ethernet  HWaddr 1c:3e:84:ea:fb:91  
          inet addr:172.20.98.67  Bcast:172.20.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7287:4a42:835e:67a7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5500 errors:0 dropped:0 overruns:0 frame:1204
          TX packets:1344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:532979 (532.9 KB)  TX bytes:164811 (164.8 KB)
          Interrupt:17 


```

---

### Post by wildmanne39 on 2016-08-04
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post, but they are not intended to be used for an entire post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

