---
title: "I would like help creating OpenVPN Bridge server for gaming."
date: 2016-04-05
forum: Networking &amp; Wireless
---

### Post by Danfun64 on 2016-04-05
Hello. I want to create an OpenVPN bridge server for gaming purposes. The reasons for this are two-fold. First, I don't want to use Hamachi because it is closed source. Second, I was hoping to record gameplay, I don't want anybody to see the external ip of either myself or the other people involved, and I don't want to deal with editing external ip's out of gameplay footage.

I don't need anything complex or fancy, I just want to make things as easy and simple as possible.

My internal IP info:
address:10.0.0.5
bcast:10.0.0.255
netmask:255.255.255.0
gateway:10.0.0.1
DNS: 75.75.75.75, 75.75.75.76

/etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

---

### Post by Danfun64 on 2016-04-07
131 views and nobody has any ideas? Or was this thread placed in the wrong place?

---

