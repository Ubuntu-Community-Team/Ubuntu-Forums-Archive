---
title: "How to configure internet connection from PC Host to mini LAB virtualbox"
date: 2015-01-13
forum: Networking &amp; Wireless
---

### Post by n3wguys on 2015-01-13
Dear All, 

I have mini lab such as

PC Host & Internet        <-----connect to internet PC host-----> VirtualBox ({PC Server Ubuntu 14.10, NAT as adapter_1, and internal Network as adapter_2}, {PC-XP,get IP from server ubuntu,it had internal network such as adapter_1).

so far, share internet from host to virtualbox(PC Server only) which had used NAT is success to ping and another task. and ping from guest to guest (VBox Server and VBox WinXP) is smoothly due from server virtual I was created dhcp server to share IP to client virtual.

my query is:

1. Forget it PC Host, because I only concentrate to virtualbox only. and here PC host only share internet from NAT virtualbox on ubuntu server
2. here virtualbox Server ubuntu that can ping inet and success.
3. I want to make an ping inet from virtualbox client but don't know get source internet from virtual server when I assume this server is PC Router Server. and how to make it. 

Thank you for your advice.

---

