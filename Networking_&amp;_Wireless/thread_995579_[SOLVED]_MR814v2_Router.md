---
title: "[SOLVED] MR814v2 Router"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by malfist on 2008-11-27
I'm at a friend's house and they asked me to set up WPA encryption on their router, but it did not provide the option. So I updated their fireware on the router from 5.03 to 5.3_05. The settings should be the same as they were before, however I cannot get a good connection through wireless. This is what happens: I connected to the wireless, and then it 'looking up xxx' for ages, often timing out. Once the connection is made, the speed is normal. I don't have any disconnects or anything like that, and they use Yahoo's DSL that's SBC (whatever that means) and use PPPoE to connect. 

Any ideas on how to resolve this issue? I've already messed with the channel and MTU with no result.

---

### Post by malfist on 2008-11-28
Here are some diagnostics:

```

jerome@ubuntu-lappy:~$ ping www.runescape.com
PING runescape.com (168.75.183.51) 56(84) bytes of data.
^C
--- runescape.com ping statistics ---
24 packets transmitted, 0 received, 100% packet loss, time 23077ms

jerome@ubuntu-lappy:~$ sudo tracert 168.75.183.51
traceroute to 168.75.183.51 (168.75.183.51), 30 hops max, 40 byte packets
 1  adsl-76-235-207-254.dsl.klmzmi.sbcglobal.net (76.235.207.254)  15.652 ms  30.338 ms *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  * ae-1-53.bbr1.Chicago1.Level3.net (4.68.101.65)  29.656 ms  30.476 ms
 7  * * *
 8  * * *
 9  * * *
10  * * *
11  * * *
12  * * *
13  * * *
14  * * *
15  * * *
16  * * *
17  * * *
18  * * *
19  * * *
20  * * *
21  * * *
22  * * *
23  * * *
24  * * *
25  * * *
26  * * *
27  * * *
28  * * *
29  * * *
30  * * *


```

---

### Post by superprash2003 on 2008-11-28
open firefox and instead of typing a website like google.com type 74.125.45.100 .. in short open [http://74.125.45.100](http://74.125.45.100) .. does the google page open up?? If it does then its mostly a DNS issue.

---

### Post by malfist on 2008-11-28
I can get to google without a problem. I figured it was a DNS issue, but I don't know how to fix it. The Router gets the DNS from the ISP so if there was a problem it should effect both wireless and wired, but the wired is fine.

When I use the IP address it doesn't time out as often.

---

### Post by malfist on 2008-11-28
I can get to google without a problem. I figured it was a DNS issue, but I don't know how to fix it. The Router gets the DNS from the ISP so if there was a problem it should effect both wireless and wired, but the wired is fine.

When I use the IP address it doesn't time out as often.

---

### Post by malfist on 2008-11-28
I changed to OpenDNS and everything is working now!

---

