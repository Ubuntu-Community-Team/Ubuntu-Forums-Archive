---
title: "Slow boot by wifi Ubuntu 18.04.4"
date: 2020-03-24
forum: Networking &amp; Wireless
---

### Post by djss---1 on 2020-03-24
Hi
My laptop boot very slow, i found the problems to fix but i don't know haw can i fix it.
In this imgs you can see the problematic services

[ATTACH=CONFIG]285275[/ATTACH]
[ATTACH=CONFIG]285276[/ATTACH]

I need help
thanks

---

### Post by ank2 on 2020-03-24
> **djss---1 said:**
> Hi
My laptop boot very slow, i found the problems to fix but i don't know haw can i fix it.
In this imgs you can see the problematic services

[ATTACH=CONFIG]285275[/ATTACH]
[ATTACH=CONFIG]285276[/ATTACH]

I need help
thanks
Suppose you mount some online device and are not online yet. Did you add something to the **/etc/fstab**&#8203; ?

---

### Post by djss---1 on 2020-03-24
i don't know, i'm new in this OS.
How can i check that?

---

### Post by ank2 on 2020-03-24
> **djss---1 said:**
> i don't know, i'm new in this OS.
How can i check that?
[QUOTE=djss---1]Hello
I post the boot problem
Can you tell me a complete option to configure or re-configure the network connection to fix the problem in the laptop boot?
I tried to disable thouse services, but i guess is not possible.
For me this OS is a little bit difficult
Thank you[/QUOTE]
If you have not changed settings in the /etc/fstab I have no idea what's wrong.

While booted, remove Samba and other services, connecting Linux with other services. After every boot, connect them manually.

---

