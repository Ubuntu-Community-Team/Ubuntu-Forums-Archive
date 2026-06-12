---
title: "cannot connect wired connection"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by jgw on 2014-06-13
I am running ubuntu 14.04  Yesterday I changed my wireless to a powerline wired connection.  It was running fine yesterday and this morning for a bit.  
The network manager tells me that I am connected at the standard 100mb/s  
I cannot ping google or yahoo (unknown host).  
Pinging 8.8.8.8 gets me destination host unreachable.  
route gets me:
destination  gateway         genmask           flags  metric  ref    use      iface
default        192.168.0.1      0.0.0.0            ug      0       0       0        eth0
192.168.0.0  *                  255.255.255.0    U       1       0       0        eth0

I tried pinging 192.168.0.1 and it replied that 192.168.0.10 was unreachable
192.168.0.1 is my router/modem (actiontech c1000a)

for the heck of it I tried to ping 192.168.0.0 and was asked "do you want to ping broadcast? then -b"

I have now started my wireless back up.  Its slow and uneven but I got back up.  Anyway, I am also wondering if my problem might be teh fact that my wireless was a powerline lan (tp-link av500)  It had been running fine for a full day before I did a speed test (at which point it suddenly failed).   I am now wondering if, perhaps, my problem is in the powerline although all the lights, etc are lit up properly and according to the documentation.

grateful for any thoughts - thank you..............

I continued to fight with this thing.  I think it was in the powerline connection.  The problem was that I had one end of the powerline plugged into a power strip.  Apparently, when dealing with a powerline connection, plugging anything into a power strip is probably a very bad idea <G>

---

### Post by Bucky Ball on 2014-06-13
*Thread moved to **Networking & Wireless**.*

---

