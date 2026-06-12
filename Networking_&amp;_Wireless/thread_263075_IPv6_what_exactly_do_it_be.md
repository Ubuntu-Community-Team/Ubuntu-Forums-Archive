---
title: "IPv6 what exactly do it be?"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by elpuerco on 2006-09-22
I have been reading the FireStarter guide and knw a bit about IPv4 and IPv6 and that the latter allows many more addresses for devices....

My laptop has etho for UTP and eth1 for wireless.  But on the Network section of the status tab under devive it lists eth0 and eth1 but also sit0 IPv6 Tunnel.

What exactly does the entry for sit0 represent/mean?

Thanks

---

### Post by jnk0906 on 2006-09-22
I'm guessing here, but I believe the additional "adapter" that you are seeing is a virtual adapter created to allow IPv6 to tunnel through the IPv4 infrastructure.  IPv6 is not a standard protocol yet and there are a LARGE number of Internet components that do not support it.  As a result, your computer creates a tunnel through the IPv4 infrastructure that allows the IPv6 connection to be made.

---

### Post by elpuerco on 2006-09-23
Thnx dude, duly noted ;)

---

