---
title: "Wifi stops working after certain period of time."
date: 2007-02-08
forum: Networking &amp; Wireless
---

### Post by zzzname on 2007-02-08
I am using Edgy on my Thinkpad X30 laptop with Aironet wireless card. On the surface it works perfect but after a certain period of time (sometimes 1 hour, sometimes 10 minutes, sometimes 5 hours) my wireless connections stops working. Only rebooting the computer makes it work again. But of course, that solution is already starting to get on my nerves. There is no response from the router so I suspect that there's something wrong with my wireless card. If anybody could help me I woud be grateful.

---

### Post by zzzname on 2007-02-09
I'll just up this thread once.

---

### Post by saris on 2007-02-09
I'm having the same problem...any feedback would be greatly appreciated :)

---

### Post by zzzname on 2007-02-09
Ok, I have found another solution now. It's not perfect but still better than rebooting your computer every single time it happens.

You've got to type:

depmod -a
modprobe -r airo
modprobe airo
ifdown eth1
ifup eth1

Where airo is my kernel module for wireless card and eth1 is my wireless interface. It's still not the most convenient thing but when I made an alias to do all these commands for me I can manage. Still, if anyone know a better solution for that problem it would be great.

---

