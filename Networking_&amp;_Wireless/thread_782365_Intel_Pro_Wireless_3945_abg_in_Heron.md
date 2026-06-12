---
title: "Intel Pro Wireless 3945 abg in Heron"
date: 2008-05-04
forum: Networking &amp; Wireless
---

### Post by Rohit507 on 2008-05-04
Hello,

I have been having problems with my Intel Pro Wireless 3945 ABG car in my HP Pavilion dv9000 laptop.

I know that the driver for this card have been integrated into the kernel and that all should work automatically, but my is Ubuntu install won't even see the card. 

This might seem simple but it is complicated by the fact that i installed this card in place of the original Broadcom Wireless card that came with the machine.

This was because the original didn't respond correctly (even in windows) and we believed this was a problem with the card itself.

As of right now i'm running only ubuntu 8.04 on the machine. 

I can't seem to figure out if this is a software issue or a hardware issue, and i would like your help with the problem.

Thanks Much :)

Rohit507

---

### Post by chili555 on 2008-05-04
```
sudo apt-get install linux-backports-modules-hardy-generic
```That seems to have fixed a lot of people here. Let us know.

---

