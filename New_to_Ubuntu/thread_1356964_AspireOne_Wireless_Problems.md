---
title: "AspireOne Wireless Problems"
date: 2009-12-16
forum: New to Ubuntu
---

### Post by Maple1987 on 2009-12-16
Hello,

I'm sure this has already been answered before, but I can't find it. 

I bought an Acer AspireOne about six months ago and haven't been able to get Ubuntu 9.04 to connect to my wireless network. I'm not sure if I'm having wireless driver problems, or I just don't know how to connect to a wireless network using Ubuntu. I've found numerous forum posts about how to solve the problem, but none of the solutions offered have been able to help.

I'll be happy to provide any information needed, and I'd appriciate any help anyone can offer.

Thanks.

---

### Post by spiderbatdad on 2009-12-16
need to know if you have the atheros wireless card.
See documentation here for enabling it.
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
blacklist acer_wmi in /etc/modprobe.d/blacklist
then restart.

---

### Post by northern lights on 2009-12-16
Please post the output of```
sudo lshw -C network && ifconfig && iwconfig
```

Thank you.

---

