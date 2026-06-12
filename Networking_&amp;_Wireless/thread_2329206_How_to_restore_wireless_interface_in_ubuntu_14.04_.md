---
title: "How to restore wireless interface in ubuntu 14.04 lts?"
date: 2016-06-28
forum: Networking &amp; Wireless
---

### Post by Praytic on 2016-06-28
Once I installed Ubuntu 14.04 lts, I discovered connection problems (supposedly with my adapter driver) and tried to solve it by googling the problem and somehow removed my wireless interface... How can I restore it?
Here is the commands which i've done before rebooting and discovering the problem:
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtlwifi-new-dkms linux-firmware
```
ifconfig doesn't show me wireless interface.

---

### Post by mörgæs on 2016-07-01
Why did you install 14.04 and not 16.04?

---

