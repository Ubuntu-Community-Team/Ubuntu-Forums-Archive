---
title: "Bluetooth firmware load... doesn't"
date: 2017-10-30
forum: Networking &amp; Wireless
---

### Post by csdgbas on 2017-10-30
[PHP]bluetooth hci0: Direct firmware load for rtl_bt/rtl8821a_config.bin failed with error -2[/PHP]

This isn't the end of the world, I don't want Bluetooth on, not ever.  How do I stop the system trying to load this please?

---

### Post by jeremy31 on 2017-10-30
Blacklist the btusb module with
```
echo "blacklist btusb" | sudo tee /etc/modprobe.d/bluetooth.conf
```

---

### Post by csdgbas on 2017-10-31
Worked perfectly. Thank you.

---

