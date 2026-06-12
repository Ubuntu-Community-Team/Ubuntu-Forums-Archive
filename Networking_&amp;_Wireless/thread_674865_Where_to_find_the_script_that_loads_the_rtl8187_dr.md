---
title: "Where to find the script that loads the rtl8187 driver"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by hahahan on 2008-01-22
I compiled and installed the rtl8187 driver from aircrack-ng.org. It works plug and play but the ieee80211-tkip and ccmp modules are not loaded automaticaly (they work insmodded manualy).
Can anyone tell me where I can find the script responsible for loading the modules in Ubuntu 7.10

Tx in advance

---

### Post by chili555 on 2008-01-22
Please try putting these in /etc/modules. Here is an excerpt from the file:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line.
```

---

### Post by renzokuken on 2008-01-22
try

```
/etc/modules
```

write them in that file then reboot and see if it works

---

