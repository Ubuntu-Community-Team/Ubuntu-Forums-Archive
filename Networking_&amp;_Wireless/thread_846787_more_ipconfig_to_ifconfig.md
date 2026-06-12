---
title: "more ipconfig to ifconfig"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2008-07-01
What is the linux (ubuntu) equivalent of "ipconfig /release" and then "ipconfig /renew" I would like to create a quick script to release and renew the IP.

---

### Post by damis648 on 2008-07-01
See the documentation of iwconfig and ifconfig with
```
iwconfig --help
```
and
```
ifconfig --help
```
in terminal.

---

### Post by kevdog on 2008-07-01
Release IP address
sudo dhclient -r <interface such as eth0, wlan0, etc>

Renew DNS lease
sudo dhclient <interface>

---

### Post by ant2ne on 2008-07-01
> **damis648 said:**
> See the documentation of iwconfig and ifconfig with
```
iwconfig --help
```
and
```
ifconfig --help
```
in terminal. :confused: Did you just read the thread title?

> **kevdog said:**
> Release IP address
sudo dhclient -r <interface such as eth0, wlan0, etc>

Renew DNS lease
sudo dhclient <interface>:KS   Very helpful!! Just what I needed.

---

