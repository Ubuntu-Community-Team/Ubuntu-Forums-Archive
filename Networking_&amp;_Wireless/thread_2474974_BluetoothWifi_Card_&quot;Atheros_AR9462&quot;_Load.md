---
title: "Bluetooth/Wifi Card &quot;Atheros AR9462&quot; Loading patch file failed"
date: 2022-05-13
forum: Networking &amp; Wireless
---

### Post by daring-t on 2022-05-13
Hello, I have a old Acer Aspire T Model: ATC-605-UR20 That uses a  Atheros AR9462 WIFI/Bluetooth card and Last week I installed Ubuntu and  everything is working but the Atheros AR9462 card. 
Reseeding the card does not help and I don't think the card is faulty because in Windows it works somewhat fine.

Device name: Atheros AR5B22
Model: AR5B22
BD ID: 18CF5EE14AD3
S/N: 18CF5EE14AD3

When starting up the PC I get:
```

/dev/sdb5: clean, 209929/3170304 files, 3410545/12668672 blocks
[    2.916082] Bluetooth: Patch file not found ar3k/atthrBT_0x11020000.dfu
[    2.916116] Bluetooth: Loading patch file failed
[    3.374401]

```

Here are the results of running the ***lsusb*** command:
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard SK-8115
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 005: ID 04ca:3006 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Any Ideas on this issue would be useful


Thanks,
Daring_t

---

### Post by jeremy31 on 2022-05-13
If this is on Ubuntu 22.04, the easy fix is to enable proposed repositories in Software and Updates, then reinstall the linux-firmware package

---

### Post by mIk3_08 on 2022-05-13
> **daring-t said:**
> Hello, I have a old Acer Aspire T Model: ATC-605-UR20 That uses a  Atheros AR9462 WIFI/Bluetooth card and Last week I installed Ubuntu and  everything is working but the Atheros AR9462 card. 
Reseeding the card does not help and I don't think the card is faulty because in Windows it works somewhat fine.

Device name: Atheros AR5B22
Model: AR5B22
BD ID: 18CF5EE14AD3
S/N: 18CF5EE14AD3

When starting up the PC I get:
```

/dev/sdb5: clean, 209929/3170304 files, 3410545/12668672 blocks
[    2.916082] Bluetooth: Patch file not found ar3k/atthrBT_0x11020000.dfu
[    2.916116] Bluetooth: Loading patch file failed
[    3.374401]

```

Here are the results of running the ***lsusb*** command:
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 003: ID 413c:2003 Dell Computer Corp. Keyboard SK-8115
Bus 003 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 003 Device 005: ID 04ca:3006 Lite-On Technology Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


Any Ideas on this issue would be useful


Thanks,
Daring_t

Just try to install Blueman for your Bluetooth. You can see blueman in your Ubuntu Software. Maybe it might work. Regards and Cheers.

---

### Post by daring-t on 2022-05-13
Thank you mIk3_08 and  		jeremy31, I thought I checked for updates before I created this thread, but I updated Ubuntu and its seems it fixed the issue.



Again that's for the help.,
Daring_T

---

### Post by mIk3_08 on 2022-05-14
> **daring-t said:**
> Thank you mIk3_08 and          jeremy31, I thought I checked for updates before I created this thread, but I updated Ubuntu and its seems it fixed the issue.
Again that's for the help.,
Daring_T Grate. Good Luck and Welcome to Linux World. Regards and Cheer.

---

