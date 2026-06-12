---
title: "Problems mounting a nokia 6233 phone with cable"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by heroidi on 2010-01-10
My brothers phone's memory card gets mounted in gNewSense but not in ubuntu 9.04 nor in 9.10 any help, it shows up in lsusb as 
```
Bus 002 Device 005: ID 0421:0492 Nokia Mobile Phones
```

---

### Post by cariboo on 2010-01-10
What is the output of dmesg, when you plug the phone in? Open a terminal and type:

```
dmesg | tail -n15
```

after you plug the device in.

---

