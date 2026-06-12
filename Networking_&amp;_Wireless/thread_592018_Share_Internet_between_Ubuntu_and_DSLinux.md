---
title: "Share Internet between Ubuntu and DSLinux"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by kman89zero on 2007-10-26
I have a laptop (ubuntu 7.10) using a wifi connection and would like to allow my desktop (Damn Small Linux 3.3) to access the internet through my laptop. I would like to accomplish this by using an Ethernet connection between the two. I have no idea where to even start. Thanks in advance for any help you can provide to me.

---

### Post by jfrorie on 2007-10-28
> **kman89zero said:**
> I have a laptop (ubuntu 7.10) using a wifi connection and would like to allow my desktop (Damn Small Linux 3.3) to access the internet through my laptop. I would like to accomplish this by using an Ethernet connection between the two. I have no idea where to even start. Thanks in advance for any help you can provide to me.

I believe the correct approach would be the change the gateway in your DSL boxes default route to forward packets through the laptops IP.  The 'route' command will allow you to do it, but I'm hazy on the syntax. (route del ... then route add...)  I also not sure if the changes are persistent.  You may need to change a file to make it so.

---

