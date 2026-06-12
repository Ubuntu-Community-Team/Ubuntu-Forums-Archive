---
title: "PPPOE goes inactive"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by y-man on 2006-10-15
Hi everyone,

I am a two-days-fresh Ubuntu user. Do have a long Linux history though.

I have Kubuntu 6.0.0.1 install, and using Konqueror for web access.

After some period of inactivity on the network, Konqueror does not connect to any server at all: "Error while loadiing ..." appears for all attempts.

At that state ifconfig still shows ppp0 as active, with no errored or dropped packets. Yet I have to poff/pon again to be able to access the internet.

Is there any explanation for this? What can I do to stop this behaviour?

Thanks,

Y-man

---

### Post by adwait on 2006-10-15
When that happens, try looking at the /etc/resolv.conf. Does it contain the proper DNS servers? Sometimes those get overwritten by some process. If so, set it to readonl by using the immutable bit
```
sudo chattr +i /etc/resolv.conf
```

---

