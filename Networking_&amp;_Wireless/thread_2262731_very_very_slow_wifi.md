---
title: "very very slow wifi"
date: 2015-01-26
forum: Networking &amp; Wireless
---

### Post by Radhames_Gomez on 2015-01-26
So I havent used linux for years and I am having a problem that seems to be very common. Extremely slow wifi. Im posting this from the computer with linux so it does works, just slower than Dial Up and very unstable.

Its an almost fresh install of ubuntu 14.04, but I think I did a few changes from another thread with another Atheros adapter.

Not sure what info is needed, but I saw that people sometimes asked for this in some of the post that I saw on the internet.

lspci -nn | grep 0280
```
03:00.0 Network controller [0280]: Qualcomm Atheros AR93xx Wireless Network Adapter [168c:0030] (rev 01)

```

---

### Post by kc1di on 2015-01-27
Hi Radhames_Gomez and welcome to Ubuntu Linux,

try the suggestions in answer #1[ here.]("http://askubuntu.com/questions/572516/get-qualcomm-atheros-ar93xx-wireless-network-adapter-to-work-under-ubuntu-14-04")

---

### Post by Radhames_Gomez on 2015-01-27
After doing the last 2 commands the wifi was trying to auto connect, but it couldnt. After a reboot, its the same way as before. Slow, to say the least.

---

