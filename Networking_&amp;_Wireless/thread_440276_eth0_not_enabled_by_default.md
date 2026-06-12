---
title: "eth0 not enabled by default"
date: 2007-05-11
forum: Networking &amp; Wireless
---

### Post by sycamorex on 2007-05-11
Hi,
I've installed Ubuntu and eth0 is not activated by default. Every time I switch on the computer I 
have to type: ifup eth0

Where can I add this command to enable it on boot-up?

thanks

---

### Post by joft on 2007-05-11
Hmmm, perhaps the line "auto eth0" is missing in /etc/network/interfaces ?

---

### Post by sycamorex on 2007-05-11
Right! thanks,
Yes I did remove it.
thanks

---

