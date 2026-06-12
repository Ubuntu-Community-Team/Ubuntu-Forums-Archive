---
title: "Bluetooth not activating (Ubuntu 14.04)"
date: 2015-05-24
forum: Networking &amp; Wireless
---

### Post by Sharked on 2015-05-24
[h=2]Bluetooth not activating (Ubuntu 14.04)[/h]

---

### Post by jeremy31 on 2015-05-24
Open a terminal window(CTRL + t) then copy the command in the code box and paste it into terminal using the right mouse click or CTRL + Shift + v, you can copy the results by highlighting with mouse and using right click/copy

```
rfkill list all; uname -a; lsusb; lsmod | grep bluetooth; lspci -nnk | grep -i bluetooth; dmesg | grep -i bluetooth; dmesg | grep -i firmware
```

---

