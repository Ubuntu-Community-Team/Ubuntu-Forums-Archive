---
title: "via-rhine not working in ubuntu 7.04 without first enabling network in windows xp"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by manish_m on 2007-05-21
I have via-rhine ethernet controller. i am using ubuntu 7.04 & winxp.
i have a static ip.
when i start my pc & use ubuntu, the network connection does not work. the ping to gateway does not go through, though i have the ip.
when i use winxp & enable network card & then reboot to ubuntu. It starts working.
can somebody tell me, why is this happening & how to rectify it ?
i want to remove winxp & without this problem being solved, this is not possible.

---

### Post by chili555 on 2007-05-21
You might try *sudo gedit /etc/modules* to add:```
alias eth0 via-rhine
```Reboot and let us know. Thanks.

---

### Post by manish_m on 2007-05-23
Hi chili555,
i tried that. it did not work.
i still have to boot into win xp, enable connection,disable it, reboot to ubuntu. Then it works in ubuntu.
Booting directly, does not work for me.

---

