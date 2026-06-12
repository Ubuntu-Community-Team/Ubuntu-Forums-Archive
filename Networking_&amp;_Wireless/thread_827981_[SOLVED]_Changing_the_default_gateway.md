---
title: "[SOLVED] Changing the default gateway"
date: 2008-06-13
forum: Networking &amp; Wireless
---

### Post by shingalated on 2008-06-13
I need to change my default gateway on my server to 192.168.1.3  right now it is 192.168.1.1 
I have done "route del default" and then "route add default gw 192.168.1.3"
and that seems to work...it shows up correctly when I run the route command, but as soon as I restart the networking stack it falls back to the old default.  How do I get it to stick?

---

### Post by argail1980 on 2008-06-13
the default GW is located in the file 
```
/etc/network/interfaces
```. change it there and restart network.

---

### Post by shingalated on 2008-06-13
Thanks, that worked.

---

### Post by kakakhushi on 2010-05-12
> **shingalated said:**
> I need to change my default gateway on my server to 192.168.1.3  right now it is 192.168.1.1 
I have done "route del default" and then "route add default gw 192.168.1.3"
and that seems to work...it shows up correctly when I run the route command, but as soon as I restart the networking stack it falls back to the old default.  How do I get it to stick?

Thanks I didn't wanted it to stick ;) so this works for me

---

