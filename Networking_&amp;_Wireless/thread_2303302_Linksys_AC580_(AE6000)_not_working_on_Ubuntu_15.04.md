---
title: "Linksys AC580 (AE6000) not working on Ubuntu 15.04"
date: 2015-11-17
forum: Networking &amp; Wireless
---

### Post by d.hypercube on 2015-11-17
Hello all,

I own a Lenovo Yoga 2 13. A great laptop but the built-in wireless card (RTL8723BE) is slow and drops connections 10 times an hour.

So I decided to go for an Ethernet to USB adapter (cable works fine now) plus a USB Wireless adapter.

I got a Linksys AC580 (AE6000) but I cannot get it to work. There are multiple threads out there but I have found no solution. Does anybody have any pointers I could use?

---

### Post by jeremy31 on 2015-11-17
What have you tried to get the RTL8723be to work?  There are options like ```
echo "options rtl8723be fwlps=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
``` and reboot.  And then there is lwfinger's rtlwifi-new on github

To give us a better overview, check the sticky post "Before posting in Networking and Wireless" and run the wireless-script command and post results

---

