---
title: "Wifi not working post upgrade Broadcom BCM43142 802.11b/g/n [14e4:4365]"
date: 2015-05-19
forum: Networking &amp; Wireless
---

### Post by rohit-hirani on 2015-05-19
Hi,

I upgraded Ubunto 2 days back and then my wifi is not showing the wifi connection.
it was working fine earlier.

I have attached  wireless-info.txt file in my post
I am using Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)

---

### Post by ajgreeny on 2015-05-19
Start with the sticky thread at [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) which may show you how to solve your problem, but come back again if it is not the answer.

---

### Post by Hadaka on 2015-05-19
Hi, your wireless info text file is showing a hardblock
```
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: [COLOR=#ff0000]yes[/COLOR]

```
please press fn/f2 keys together ONE time then
from a wired working connection
please open a terminal..ctrl/alt/t and do.
```
sudo apt-get update
sudo rfkill unblock all
sudo rm /etc/udev/rules.d/70-persistent-net.rules
```
boot
then do..
```
rfkill list all
```
is it still showing a hardbolock?

---

### Post by rohit-hirani on 2015-05-24
Its working with the help of ctrl and F2,
Thanks for your help

---

### Post by Hadaka on 2015-05-24
Glad you found the solution !!
please sign back in and mark your thread SOLVED
by clicking >>thread tools>>solved
thanks

---

