---
title: "Internal LAN HP Pavilion 15 not working"
date: 2014-11-05
forum: Networking &amp; Wireless
---

### Post by edmondkreuk on 2014-11-05
Hi, I recently bought a HP Pavilion 15 n-038sf (french version) with Windows 8. 

I had some problems with the internal LAN adapter, but was able to work on wifi. 

Yesterday I installed Ubuntu 14.10 and can not find out how to get my LAN connection back to life... I have wifi.

---

### Post by papibe on 2014-11-05
Hi edmondkreuk. Welcome to the forum ):P

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
sudo lshw -C network

lspci -nnk | grep -iA2 net
```
Regards.

---

### Post by jeremy31 on 2014-11-05
Dupe

---

