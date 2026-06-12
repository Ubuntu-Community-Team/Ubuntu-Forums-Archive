---
title: "gutsy only loads some websites"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by Melganis on 2007-11-01
alright, this is a pretty weird problem. just upgraded to gutsy today after commenting out the wine.lowvoice.nl line from sources.list that automatix put there (it made the upgrade fail) and now i cant access some websites. earlier today, on feisty, they worked fine. now, on gutsy, some don't. fortunately, ubuntuforums.com works, unfortunately, google.com isn't. this is on a wired connection. ifconfig looks like this:

```
[CODE]spencer@codemonkey:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:C0:A8:86:AB:C3  
          inet6 addr: fe80::2c0:a8ff:fe86:abc3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141181 (137.8 KB)  TX bytes:60276 (58.8 KB)
          Interrupt:20 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:0F:B3:32:16:4B  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b3ff:fe32:164b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2651 errors:1 dropped:0 overruns:0 frame:1
          TX packets:2426 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2107403 (2.0 MB)  TX bytes:411968 (402.3 KB)

eth0:avah Link encap:Ethernet  HWaddr 00:C0:A8:86:AB:C3  
          inet addr:169.254.10.30  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15438 (15.0 KB)  TX bytes:15438 (15.0 KB)

```[/CODE]

anyone have any ideas?

---

### Post by QTRFy on 2007-11-01
This maybe a FireFox problem.  From:

[http://kb.mozillazine.org/Error_loading_some_websites](http://kb.mozillazine.org/Error_loading_some_websites)


The problem may be with IPv6 ("Internet Protocol version 6"). To disable IPv6, change the preference network.dns.disableIPv6 from "false" to "true" . Here are the steps:

   1. Type about:config in the address bar, press Enter.
   2. Find network.dns.disableIPv6 in the list.
   3. Right-click -> Toggle.
   4. Restart Firefox/Mozilla Suite and try again. 

If this doesn't work, re-enable IPv6 by resetting the preference to "false".

---

### Post by Melganis on 2007-11-01
no, the problem was with all my browsers, not just firefox, but disabling the IPv6 made it work, thank you. I hope that someday I can contribute to someone as you have to me :)

---

