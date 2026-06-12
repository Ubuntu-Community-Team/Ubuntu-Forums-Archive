---
title: "Problems with RTL8812au driver"
date: 2020-12-07
forum: Networking &amp; Wireless
---

### Post by SeijiSensei on 2020-12-07
I have a friend's Lenovo laptop for which we bought an [RTL-8811au based USB wifi dongle]("https://www.amazon.com/TP-Link-Mini-Wireless-Supports-10-9-10-14/dp/B07PB1X4CN/").  It's about eight years old.  I also own a Lenovo Y570 of about the same vintage.

On my system, running Kubuntu 20.04, I can install the RTL8812au driver with "sudo apt install rtl8812au-dkms" or select it from the Driver Manager. The kernel module compiles and, once installed, supports both my [TP-Link 802.11ac USB adapter]("https://www.amazon.com/gp/product/B00D0AF3TA/") and the slower but more compact 8811-based dongle we bought for his computer.

On his computer I get nada. I installed a fresh version of 20.04 in a separate partition (he was on 18.04) and followed the identical steps. Neither my adapter nor his is recognized by the system.  I've pulled my metaphorical hair out over this for a day or two.  Is it possible that his laptop has some hardware feature that makes it fail when mine works?

I've also tried a different [8812au driver from GitHub]("https://github.com/abperiasamy/rtl8812AU_8821AU_linux") with no success.

It does work with two N devices I tried, an Edimax dongle and a TP-Link TL-WN722N USB device. Both use the Atheros chipset and are supported by the standard kernel.  And, of course, it works fine with the motherboard adapter, a Broadcom.

---

### Post by praseodym on 2020-12-07
Deactivated SecureBoot? The driver may not be signed

---

### Post by SeijiSensei on 2020-12-07
Yup. Just checked, and it's disabled.

Thanks for the suggestion though.

I can see the driver if I activate it with insmod or modprobe then use lsmod. Even with it in the module list, the adapters are just ignored.

---

### Post by praseodym on 2020-12-07
Ok, please show
```

lsusb
lsmod
rfkill list
iwconfig
```

---

### Post by SeijiSensei on 2020-12-07
> **praseodym said:**
> Ok, please show
```

lsusb
lsmod
rfkill list
iwconfig
```
I'm about to return the laptop to its owner, so I'm not sure I can do all this. Both devices I tried appear with lsusb and, as I said, lsmod shows that the module is loaded into the kernel.

I'll have another shot at it later on, so I can run those last two commands.  I'm not sure either will show us much since, as I reported, inserting either adapter does nothing.

---

### Post by jeremy31 on 2020-12-07
When you get your hands on it again see what ```
tail -f /var/log/syslog
```
Shows when the adapter is plugged in
I think rtl8812au-dkms still has broken dkms and there might be other issues on a new install if you install any dkms driver package after installing a new kernel but before a reboot

---

