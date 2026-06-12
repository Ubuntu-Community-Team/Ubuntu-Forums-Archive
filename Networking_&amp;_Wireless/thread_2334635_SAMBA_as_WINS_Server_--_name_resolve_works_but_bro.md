---
title: "SAMBA as WINS Server -- name resolve works but browsing only one subnet?"
date: 2016-08-21
forum: Networking &amp; Wireless
---

### Post by naldinho on 2016-08-21
I am using IPsec to create a site-to-site VPN between 10.1.1.0/24 and 192.168.2.0/24 -- this works fine.

Both networks have a mix of Windows and Linux machines (most ubuntu or ubuntu variants + 1 CentO/S and 2 Unraid). 

I have installed samba on a VM that has ubuntu server on 192.168.2.0 and changed all the computers to use it as a WINS server. 

The result is that all computers on either network have name resolution for all computers. When it comes to network browsing though only computers on 10.1.1.0 can see all computers regardless of subnet but computers on 192.168.2.0 can only see computers on 192.168.2.0

If I reverse the situation and setup an ubunto server on 10.1.1.0 as a WINS server I then get the opposite result -- all computers can name resolve but only computers on 192.168.2.0 can cross-subnet browse.

I feel like I must be close but searching for an answer I can't find anything -- and actually found someone on this forum having the exact same problem just a week ago (he got no responses).

Can anyone point me in the right direction?

---

