---
title: "[SOLVED] Bluetooth in Ubuntu Studio on T61 ThinkPad"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by gorgon on 2008-02-26
Hi there,

I read around that bluetooth is supposed to work out of the box in 7.10 on a T61 ThinkPad, but I can't find it anywhere.. The bluetooth light is lit (I can turn it on/off), but it's not in the upper panel and does not appear when I try to add the 'notification area'. Looking for my pc from an other bluetooth device can't find any.

I tried:

```

$ sudo modprobe thinkpad_acpi
$ sudo -i
# echo enable > /proc/acpi/ibm/bluetooth
```
but nothing happened.

Any ideas?
cheers,

---

### Post by gorgon on 2008-07-08
trying to clean up an olt thread. I think I solved this by installing a library, bluez or something.

---

