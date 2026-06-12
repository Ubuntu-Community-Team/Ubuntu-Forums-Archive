---
title: "Wireless quit"
date: 2014-04-16
forum: Networking &amp; Wireless
---

### Post by Poly Hive on 2014-04-16
I managed to install the driver for my USB wireless card (I know it is not a card but cannot think what the tech word is). However it has stopped working. I have the driver folder on my desk top but hneed the code to install it please. The chip is an RTL8111 

any help much appreciated. 

PH

---

### Post by praseodym on 2014-04-16
Hi,

RTL8111 is your LAN card. Does it work?

Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
cat /etc/resolv.conf
rfkill list
```
What kind of computer is it?

---

### Post by Poly Hive on 2014-04-16
I will try that code but am unable to copy and past as I am using my lappie to connect here. Obviously there is no connection from the lan card on the puter which is a very elderly machine of no particular make as it was an Ebay machine in it's day as in a vendor on there. 

PH

---

