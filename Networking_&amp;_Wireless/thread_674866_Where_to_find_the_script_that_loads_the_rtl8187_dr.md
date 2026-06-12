---
title: "Where to find the script that loads the rtl8187 driver"
date: 2008-01-22
forum: Networking &amp; Wireless
---

### Post by hahahan on 2008-01-22
I compiled and installed the rtl8187 driver from aircrack-ng.org. It works plug and play but the ieee80211-tkip and ccmp modules are not loaded automaticaly (they work insmodded manualy).
Can anyone tell me where I can find the script responsible for loading the modulesin ubuntu 7.10

Tx in advance.

---

### Post by benzo8 on 2008-01-22
Add the module names (and any parameters) to /etc/modules

---

### Post by hahahan on 2008-01-22
Tx, that works, But to be honest I'm still curious where and when Ubuntu loads them, just for learning.
Any idea where to look?

---

### Post by benzo8 on 2008-01-22
Have a look at ```
/etc/init.d/module-init-tools
``` ... This script handles the loading for the modules listed in /etc/modules. It is called during boot, from the symlink ```
/etc/rcS.d/S15module-init-tools
```

---

### Post by hahahan on 2008-01-22
Tx, but not exactly what I'm looking for. This loads the modules mentioned in /etc/modules at boot time, but how ubunto loads the other r8187 modules when I plug in the usb-device.

---

