---
title: "Ralink Wireless Disconnects after some minutes and does not connects again until rest"
date: 2013-09-20
forum: Networking &amp; Wireless
---

### Post by abdulroqeeb on 2013-09-20
I just moved from windows to ubuntu linux and I have been having a bunch of problem most of which I have been able to fix. However, I have a problem with my wireless network as it disconnect after some minutes and will not be able to connect again until I restart the system. I have tried to unistall the driver and install the rt3290 driver from ralink but this failed giving that it cannot stat. I don't really understand the problem and would want a fast solution. My system is HP 655 using Ralink RT3290. Í am running ubuntu 13.01 saucy salamder. Thank You

---

### Post by SamTarling on 2013-09-20
Hey there,

This particular wireless device seems to have some problems, though there are some solutions [here]("http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working") (have you tried them?) and some further discussion on [this thread]("http://ubuntuforums.org/showthread.php?t=2104129")

*Apparently* this issue is fixed in 13.10..

---

### Post by abdulroqeeb on 2013-09-21
Thanks for your time but I am actually running 13.10 and it detects wireless but after some minutes of connection, it just disconnects and never reconnects until restart. The link you gave is for 12.04 and ealier where wireless is not detected at all. Is it possible to just remove the default driver and re install it with the official driver from Ralink? Thanks.

---

### Post by blusa on 2013-10-14
I suppose it's a bug in the new 3.11 kernel. Have you found a solution? I have the same problem on a asus x200ca with rt3290 wifi chipset.
yesterday i reported the bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239459](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1239459)

---

### Post by jdafoe1 on 2013-10-23
Workaround here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466). Comment #116 & 117.

---

