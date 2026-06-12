---
title: "c821 wireless network adapter not detected in Ubuntu 17.10"
date: 2017-12-18
forum: Networking &amp; Wireless
---

### Post by nallasamy.sathya on 2017-12-18
Wireless network adapter is not detected and so both wifi & bluetooth not working in my new lenevo thinkpad E470 running ubuntu 17.10. 
[B]
lspci:[/B]
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c821
sathya@ThinkPad-E470:~$ lspci -v -s 05:00.0

**lspci -v -n -s 05:00.0**
05:00.0 0280: 10ec:c821
    Subsystem: 17aa:c024
    Flags: fast devsel, IRQ 255
    I/O ports at c000 [disabled] [size=256]
    Memory at f1000000 (64-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>
I am not finding appropriate network controller drivers online. Please help me to fix this issue.

---

### Post by jeremy31 on 2017-12-18
Moved to Networking

---

### Post by praseodym on 2017-12-18
See here:

[https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710](https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710)

---

### Post by chili555 on 2017-12-30
Or see here: [https://askubuntu.com/questions/990378/wifi-not-working-on-lenovo-thinkpad-e570](https://askubuntu.com/questions/990378/wifi-not-working-on-lenovo-thinkpad-e570)

---

