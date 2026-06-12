---
title: "HP DV2129ea + Edgy = ipw3945 not working :("
date: 2006-11-25
forum: Networking &amp; Wireless
---

### Post by garbage_ on 2006-11-25
Ok, I have bought a lovely HP DV2129ea and it is very nice indeed.
I rushed to install Edgy on it and it worked great, but...
wireless doesn't work, here is a summary:
It has an Intel 3945ABG wireless card and I have installed "ieee80211" and the restricted modules for the kernel.
Still, only wired networking exists - just eth0, not eth1 or anything else.
This is the "dmesg | grep ipw":
```

ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
ipw3945: Copyright(c) 2003-2006 Intel Corporation
ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)

```

here is "lsmod | grep ipw" output:
```

ipw3945               124576  1 
ieee80211              35272  1 ipw3945

```

It seems that the card is recognized, but still not present in the interfaces list.

any ideas?

---

### Post by zgornel on 2006-11-25
Is the wireless adapter present in System/Administration/Networking ?

---

### Post by garbage_ on 2006-11-25
No it is not there, this is why it is so weird.

---

### Post by zgornel on 2006-11-25
Try adding 
[I]auto eth1
iface eth1 inet dhcp
[/I]
in /etc/network/interfaces and reboot. Watch dmesg for info about eth1.

---

### Post by garbage_ on 2006-11-26
Thanks - the addition of eth1 helped it :)

after that, I have installed Network Manager and it required me to
erase it, but nonetheless - thank you.

---

### Post by zgornel on 2006-11-26
Good. Strange anyways ...

---

