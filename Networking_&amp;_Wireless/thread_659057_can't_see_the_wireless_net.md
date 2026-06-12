---
title: "can't see the wireless net"
date: 2008-01-05
forum: Networking &amp; Wireless
---

### Post by clf99 on 2008-01-05
ok.  7.10 is installed.  win2k could see the wireless networks around here.  but this guy cannot.
where would you start in diagnosing this one?

it sees the usb wireless adapter and thinks it's talking to it but i see no networks

---

### Post by ugm6hr on 2008-01-05
> **clf99 said:**
> ok.  7.10 is installed.  win2k could see the wireless networks around here.  but this guy cannot.
where would you start in diagnosing this one?

it sees the usb wireless adapter and thinks it's talking to it but i see no networks

Some basic info - the output from the following:
```
lsusb -v
lshw -C network
iwconfig
iwlist scan
```

---

