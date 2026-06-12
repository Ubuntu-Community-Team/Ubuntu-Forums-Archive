---
title: "no scan results..."
date: 2007-12-12
forum: Networking &amp; Wireless
---

### Post by buccaneere on 2007-12-12
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**[COLOR="Red"]eth1      No scan results[/COLOR]**

sit0      Interface doesn't support scanning.


What's not right here?

Thanks

---

### Post by Lostincyberspace on 2007-12-12
Run ifconfig and post the results.

---

### Post by buccaneere on 2007-12-12
Hi Lost...

What exactly does this tell me? The reason I ask, is cause I still got two more wireless machines (HP laptop + desktop homebuild with wireless card) besides this one (Gateway MX6xxx), and want to know what to look for when I config'em. Someone else helped me with my first one (Acer 5000), but I didn't learn what I did, as I did it. So I can't help myself again, OR OTHERS:(

So I'm back. Thanks

chuckb@chuckb-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:B8:A7:85:CC  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fea7:85cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:329258 (321.5 KiB)  TX bytes:23735 (23.1 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:14:A5:42:B7:B6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:e0208000-e020a000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by buccaneere on 2007-12-12
The interface is now executing a scan.:confused: I changed some settings; really wish I knew which ones too, cause I still got two more machines to configure after this one...

Thanks there Lost!

---

### Post by CheshireMac on 2008-01-03
Alright, so I'm having the same scan issue, with no results, and ifconfig doesn't show eth1, although the scan does. 
This is all happening on a different machine than what I'm used to, but I got my own running wifi without using Ndiswrapper. I'm hoping I can do the same for this one, although I can't remember what I did to get mine working. ~LOL~
The machine is an Inspiron 6400 with Dual-Core, and it has a Dell mini wireless . . .I personally run on HP, and I don't know what kind of differences there would be in working this issue. 
Any thoughts would be appreciated.

---

