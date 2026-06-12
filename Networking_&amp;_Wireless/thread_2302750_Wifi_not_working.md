---
title: "Wifi not working"
date: 2015-11-13
forum: Networking &amp; Wireless
---

### Post by Dhivin on 2015-11-13
[http://pastebin.com/CEi3HzAR](http://pastebin.com/CEi3HzAR)

Please help me guys .I cant cannot connect to the wifi i am not sure what the problem is.I have posted my wireless.info here.

Thankyou

---

### Post by Hadaka on 2015-11-13
Hi, from a working wired connection please COPY and paste.
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo iw reg set IN
sudo sed -i 's/^REG.*=$/&IN/' /etc/default/crda
sudo apt-get autoremove && sudo apt-get autoclean
sudo modprobe wl
```
disconnect wired connection,and test wireless

---

