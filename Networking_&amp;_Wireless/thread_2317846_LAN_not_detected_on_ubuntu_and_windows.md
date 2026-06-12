---
title: "LAN not detected on ubuntu and windows"
date: 2016-03-20
forum: Networking &amp; Wireless
---

### Post by saptarshibanikods on 2016-03-20
Everything was fine when one morning I woke up,turned on the pc and none of the two os could detect my lan. Replugged in. Tried installing the drivers but no use. Why did this not work can someone help.

---

### Post by praseodym on 2016-03-20
Please open a terminal with CTRL+ALT+T and show the outputs of these commands

```
lspci -nnk
lsmod
ifconfig -a
cat /etc/resolv.conf
route -n
```

---

### Post by ajgreeny on 2016-03-20
Sounds as if your modem/router has died since both Windows and Ubuntu are not seeing it.

Try rebooting that to see if it comes to life again.

---

