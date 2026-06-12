---
title: "Ndiswrapper problem"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by icechen1 on 2007-05-18
Hi,
I don't know what i do,but now each time i open ubuntu,the wireless(using ndiswrapper) stopped working(it was working 30 min ago),now each time i boot i have to go to terminal and tape
```
sudo modprobe ndiswrapper
```
and the wireless magically work after that.
If there any solution to this?

---

### Post by icechen1 on 2007-05-18
Fixed,i did:
```
sudo gedit /etc/modules

```
and added ndiswrapper in that file

---

