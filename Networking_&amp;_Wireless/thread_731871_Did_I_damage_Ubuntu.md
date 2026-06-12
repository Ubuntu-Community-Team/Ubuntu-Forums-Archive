---
title: "Did I damage Ubuntu?"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by HuBaghdadi on 2008-03-22
Hi.
Usually, I go to an Internet cafe, pick a network cable and plug it into the laptop and I'm on the net!
In the past days I tried to configure my internal modem and Huawei E220 but without any success.
Yesterday I went to the Internet cafe and plugged the cable into the laptop but this didn't work.
No connection at all.
Did I damage my Ubuntu (7.10) when I tried to configure the modem and E220?

---

### Post by Sam Lars on 2008-03-22
Yes, there's a good chance that in fiddling with the modem you changed something with the ethernet.
What do you get from
```
ifconfig
```
and what is in your
```
/etc/network/interfaces
```

---

### Post by HuBaghdadi on 2008-03-23
eth0      Link encap:Ethernet  HWaddr 00:1C:23:94:A0:A5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16301 (15.9 KB)  TX bytes:16301 (15.9 KB)


/etc/network/interfaces
auto lo
iface lo inet loopback

Please note that I run ifconfig command when I was not connected to anything (no Wi-Fi, no Bluetooth, nothing at all).

---

### Post by Sam Lars on 2008-03-23
Try adding
```
iface eth0 auto dhcp
auto eth0
```
to the interfaces file.

---

