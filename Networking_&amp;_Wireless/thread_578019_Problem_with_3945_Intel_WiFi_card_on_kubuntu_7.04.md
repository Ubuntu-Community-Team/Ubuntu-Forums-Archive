---
title: "Problem with 3945 Intel WiFi card on kubuntu 7.04"
date: 2007-10-16
forum: Networking &amp; Wireless
---

### Post by smk666 on 2007-10-16
Hi i recently switched from ubuntu to kubuntu, by the reason of not working wireless card. Altough i see some progress, the wlan isn't working, in fact the eth interface isn't seen by iwconfig. Thanks in advance for any help :) And here are some logs:

```

smk@smk-laptop:~$ dmesg | grep ipw
[   17.364000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.364000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.400000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   19.336000] ipw3945: Radio Frequency Kill Switch is On:

```

```

smk@smk-laptop:~$ sudo ipw3945d-2.6.20-16-generic
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
Intel PRO/Wireless 3945ABG Network Connection found at:
 /sys/bus/pci/drivers/ipw3945/0000:10:00.0
Daemon launched as pid 5904.  Exiting.

```

```

smk@smk-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.                <--- My cable LAN card

```

---

### Post by lonelyxpeople on 2007-10-16
i have the same card, and honestly it worked for me from day one.
it *is* a restricted driver and after i installed  ubuntu for the first time, it notified me of it,

but it's been running well from day one, with the exception of some WEP problems. im running ubuntu 7.04, or for now. ;]


i dont see where your problems coming from. have you tried a clean reinstall?

---

### Post by lonelyxpeople on 2007-10-16
didnt catch this the first time!


> **smk666 said:**
> 

```

smk@smk-laptop:~$ dmesg | grep ipw
[   17.364000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.0mp
[   17.364000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   17.400000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[B][I][U][   19.336000] ipw3945: Radio Frequency Kill Switch is On:

```[/B][/I][/U]




it may be different for you, but for me i press Fn+F2, some laptops have a physical switch instead of keys to turn wifi off.

---

### Post by smk666 on 2007-10-17
I have a dedicated switch with led indicator on my hp Nx7300 notebook. At the time of taking logs LED was lit, and when I turn it off, it's switching BT off and the message isn't changing.

I made some research about the kill switch problem, but I can't find solution for my HP Compaq Nx7300... so impopular lap? :|

EDIT:
Problem was solved by resetting BIOS to factory defaults

---

