---
title: "thinkpad t60p wireless problem"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by jay576 on 2008-05-14
Ok so I've been using ubuntu for awhile on and off but i have not been able to get my wireless to connect in 8.04.  The card is fine and my wireless network is seen with the roaming networks but it won't connect to the network.  The card worked fine under 6.06 and 7.10 so I do not understand why the parts have not changed but are not working on 8.04,
thanks for the help in advanced

---

### Post by chili555 on 2008-05-14
> the parts have not changedWhich parts do you have? The Thinkpad T60p came with three different wireless cards. You can find out with:```
lspci -v | grep -i wireless
```If it's the beloved Intel 3945ABG, you can coax it to life, usually, with:```
sudo apt-get install linux-backports-modules-hardy-generic
```If it's something else, please let us know and we'll be glad to help.

---

### Post by jay576 on 2008-05-14
it is the  Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02) and that did not change anything.  It is detecting the wireless network but won't connect to the network.

---

