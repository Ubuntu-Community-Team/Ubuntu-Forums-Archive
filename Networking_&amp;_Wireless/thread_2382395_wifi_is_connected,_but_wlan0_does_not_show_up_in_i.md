---
title: "wifi is connected, but wlan0 does not show up in ifconfig or iwconfig"
date: 2018-01-12
forum: Networking &amp; Wireless
---

### Post by tr4nqu1l on 2018-01-12
Just as the title states, my laptop is connected to the internet, but when I try to run ifconfig or iwconfig wlan0 does not show up. I tried as a normal user and as the root user but still nothing. I am running Ubuntu 14.04 and I want to find my device's IP so I can ssh to it from my phone. Any help would be greatly appreciated!

---

### Post by jeremy31 on 2018-01-12
So what does iwconfig actually show?

---

### Post by praseodym on 2018-01-12
For the IP you need "ifconfig -a"

---

### Post by gordintoronto on 2018-01-14
My wifi appears as wlp4s7, and the next line shows "inet", the IP address. wlan0 was retired some years ago.

---

