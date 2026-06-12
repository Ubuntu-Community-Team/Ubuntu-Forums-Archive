---
title: "Ad hoc network without an access point in Edgy Eft"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by arinto on 2006-12-24
Dear All,

I want to set up wireless ad hoc network without access point for routing protocol testing. Basically my intended configuration is like this

Laptop 1 <<----------------->> laptop2 
using ad hoc network and static IP

what parameters that I need to set up to achieve this configuration?

Thank you

arinto

---

### Post by cilynx on 2006-12-24
```
man iwconfig
```

you need to set the essid of each so that they are the same.  you need to set each to ad-hoc mode.

```
man ifconfig
```
you need to set the ip addresses to be different but within the same netmask

let me know if you need a better explanation...best of luck

---

### Post by arinto on 2006-12-25
Dear All, 

I already tried the steps above by setting static IP, with same essid, same frequency and same channel. The laptop can ping each other. But the problem is routing protocol daemon can't get its broadcast packet to be broadcasted. When the routing protocol wants to send the broadcast packet, the linux socket function **sendto** return with error code 101 which means Network is Unreachable (definition from errno.h)

anyone has idea to solve this problem??


Thank you

Arinto

---

### Post by cilynx on 2006-12-25
I could be entirely off base here, but are you sure ad-hoc supports broadcasting?  Being a pretty pure PTP protocol, I don't know that it would have to.  Again I have nothing to back this up, just a thought.

---

