---
title: "&quot;arp&quot; command takes a while to display info"
date: 2007-07-08
forum: Networking &amp; Wireless
---

### Post by B-Con on 2007-07-08
When I type the command "arp" to view my ARP table, it takes about 7 seconds to display the table listings. 

Why is this, and is there a way to speed it up?

---

### Post by arvevans on 2007-07-08
Apparently nothing wrong with your "arp" delay.  I just ran "time arp" and got this result.

[INDENT]arv@k7hkl:~$ time arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.0.1              ether   00:09:5B:6A:0F:A2   C                     eth0

real    0m5.107s
user    0m0.004s
sys     0m0.008s
arv@k7hkl:~$ [/INDENT]

My computer is a 2.2 GHz AMD 32-bit single CPU system with 512 MB of RAM.

Arv
_._

---

### Post by B-Con on 2007-07-08
Good, it's not just me. I was wondering if something odd had messed up my ARP cache or something (experimenting with ARP poisening and such with two of my machines at the moment).

Why the delay? When I was in Windows on the same machine it took a split second to display the ARP table. Why would Linux take so much longer? What's it doing that's so time intensive?

---

