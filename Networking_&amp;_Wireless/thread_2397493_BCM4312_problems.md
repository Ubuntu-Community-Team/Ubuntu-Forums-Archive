---
title: "BCM4312 problems"
date: 2018-07-30
forum: Networking &amp; Wireless
---

### Post by tasbala on 2018-07-30
I have a triple boot system with Ubuntu 18.04, Win 7 and XP. When I originally installed Ubuntu, it didn't have wifi. I did this trick: [https://www.google.hu/url?sa=t&source=web&rct=j&url=%23&ved=0ahUKEwi2-rrVicfcAhUECpoKHZT7B4cQxa8BCCMwAA&usg=AOvVaw0VTJzWxrN8ZFOD4xbU2nov](https://www.google.hu/url?sa=t&source=web&rct=j&url=%23&ved=0ahUKEwi2-rrVicfcAhUECpoKHZT7B4cQxa8BCCMwAA&usg=AOvVaw0VTJzWxrN8ZFOD4xbU2nov) and it worked. A few days later, I boot into Windows 7, and the WiFi is not working. I tried installing drivers, but it still didn't find the card. I checked in Ubuntu, and it was the same. I tried doing the trick again, but the terminal said, it's already up to date. I shut down the computer, got the card out, and plugged it back, but this didn't change anything. Please help

---

### Post by praseodym on 2018-07-30
Please run the wireless script from the sticky thread and show the outputs

---

### Post by tasbala on 2018-07-31
Here is the result: 
[http://paste.ubuntu.com/p/5tB9qc9tKN/](http://paste.ubuntu.com/p/5tB9qc9tKN/)

---

### Post by chili555 on 2018-07-31
You have the wrong driver. With the ethernet connected, open a terminal and do:```
sudo apt purge bcmwl-kernel-source
sudo apt install firmware-b43-installer
```Reboot.

---

### Post by tasbala on 2018-07-31
The wireless hardware switch was turned off. I feel so dumb. Sorry

---

### Post by mörgæs on 2018-07-31
Good, please mark the thread solved.

---

### Post by david tutton on 2018-09-28
Thank you for this chili555:KS

---

