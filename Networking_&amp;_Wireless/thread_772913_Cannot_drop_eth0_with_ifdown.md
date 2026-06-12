---
title: "Cannot drop eth0 with ifdown"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by mhills on 2008-04-28
I need to drop my eth0 connection to the internet in order to change the connection to another computer. In earlier versions of ubuntu I used ifdown eth0, but this no longer seems to work. I get the message `eth0 not configured'. I am currently using ubuntu 7.10. What should I do to drop eth0? 

Michael

---

### Post by Iowan on 2008-04-29
[guess]/etc/init.d/networking stop [/guess]?

---

