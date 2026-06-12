---
title: "lost wifi after system stanby"
date: 2017-01-27
forum: Networking &amp; Wireless
---

### Post by elim-qiu on 2017-01-27
OS is lubuntu 16.04  (On Dell D430)

The wifi connection is good every time reboot or start the machine. But when awake from sleep, the connection is gone and the network manager app doesn't show any wifi network available near by.

Thanks for your idea and help!

---

### Post by elim-qiu on 2017-01-28
After some searching, I found the solution: 
```
sudo apt-get update
sudo apt-get dist-upgrade
```
fixed the problem....(I don't know why though)

---

### Post by elim-qiu on 2017-02-08
I found my wifi connection would drop from time to time after system stanby in some unpredictable way...

Wonder why system software updates cannot fix the problem.

---

