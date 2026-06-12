---
title: "Two NICs problem"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by marcin.mtl on 2006-10-16
I have two network interfaces in my Ubuntu. Both are working fine with one serious glitch.
First interface always comes up as eth0. Second one sometimes comes up as eth1 and another time as eth2. This pose a problem with my Ntop which is set to capture/monitor on eth1 interface. When I reboot box and it comes as eth2 instead of eth1 then Ntop is not working.
Any idea?

regards

Marcin

---

### Post by Peter76 on 2007-07-30
Funny, just replied to a thread like this .... Anyway, you can set the name of the interface according to it's MAC address in the /etc/iftab file; check:

```
man iftab
```

---

