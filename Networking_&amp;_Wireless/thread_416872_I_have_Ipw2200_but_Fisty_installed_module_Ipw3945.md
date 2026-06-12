---
title: "I have Ipw2200 but Fisty installed module Ipw3945"
date: 2007-04-21
forum: Networking &amp; Wireless
---

### Post by mexlinux on 2007-04-21
I have Ipw2200 but Fisty installed module Ipw3945
from lspci:
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

Is this normal?
Am I missing anything?

---

### Post by codingmaster on 2007-04-21
Hello!

Can you post the output of lsmod | grep ipw

works for me without problems:

gebe@venus:~$ lsmod | grep ipw
ipw2200               148040  0 
ieee80211              50412  1 ipw2200
gebe@venus:~$

Also try: modprobe ipw2200

If it will return errors, please check:

gebe@venus:~$ find /lib/modules/`uname -r` -iname ipw* | grep 2200

It will return something like, depending on your kernel version:

/lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/ipw2200.ko


Regards, Georgy Berdyshev

---

### Post by mexlinux on 2007-04-21
```

mcanedo@mcanedo-laptop:~$ lsmod | grep ipw
ipw2200               148040  0
ieee80211              34760  1 ipw2200

```

```

mcanedo@mcanedo-laptop:~$ modprobe ipw2200
mcanedo@mcanedo-laptop:~$ 

```

NOTE: The card is working, Is just that I want to use aireplay, so I'm going into the ipw2200 patching, but since I found only ipw3935 int /etc/modeprobe.d/ ....
I don't want to mess things up

---

### Post by mexlinux on 2007-04-21
```

mcanedo@mcanedo-laptop:~$ find /lib/modules/`uname -r` -iname ipw* | grep 2200
/lib/modules/2.6.20-15-generic/kernel/drivers/net/wireless/ipw2200.ko

```

---

### Post by codingmaster on 2007-04-21
Hello!

Sorry, can you explain it a bit more detailed.

Because your card is working and the kernel modules loaded.
So everything is fine and working.

I just do not know exactly, what you want to achieve:

> **mexlinux said:**
> 
NOTE: The card is working, Is just that I want to use aireplay, so I'm going into the ipw2200 patching, but since I found only ipw3935 int /etc/modeprobe.d/ ....
I don't want to mess things up

There is not modprobe.d entry for ipw2200, it works without it.

Regards, Georgy Berdyshev

---

