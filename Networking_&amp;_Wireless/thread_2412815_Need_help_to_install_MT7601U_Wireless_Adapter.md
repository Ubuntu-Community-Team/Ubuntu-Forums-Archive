---
title: "Need help to install MT7601U Wireless Adapter"
date: 2019-02-17
forum: Networking &amp; Wireless
---

### Post by c1ga on 2019-02-17
Hello Guys

I just switched from windows that means i'm new with linux and linux commands.
After i've intalled ubuntu 18.04 my wifi was working fine till the next restart, than my wifi disappeared.
I've tried with some advice that was given on earlier on some posts but still cant get it work.
Will someone be able to help me to find solution.

Thank You.

---

### Post by chili555 on 2019-02-18
Is the driver loaded?```
lsmod | grep mt76
```If not, load it:```
sudo modprobe mt7601u
```Now does your wireless work? If not, check the log:```
dmesg | grep mt76
```

---

