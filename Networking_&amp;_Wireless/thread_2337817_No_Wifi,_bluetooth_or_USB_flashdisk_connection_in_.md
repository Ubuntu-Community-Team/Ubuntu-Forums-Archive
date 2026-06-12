---
title: "No Wifi, bluetooth or USB flashdisk connection in Ubuntu 14.04"
date: 2016-09-21
forum: Networking &amp; Wireless
---

### Post by ccetin on 2016-09-21
I just bought a Dell Precision 3510 computer with Ubuntu in it. 
At first, I could not connect to wifi but I was able to see wifi options in network manager when I click on it.
Bluetooth connection was also on but I could not connect any USB flashdisks.
Then, someone helped me to get connected to wifi by changing security settings in 'edit' option of the wifi connection.
It was successful and I could connect. Then, Ubuntu asked for an update and I updated.
Now, I can't see any wifi network options or Bluetooth icon as I used to see before.
I can't also connect with an ethernet cable to wired connection due my work environment.

---

### Post by wildmanne39 on 2016-09-21
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

