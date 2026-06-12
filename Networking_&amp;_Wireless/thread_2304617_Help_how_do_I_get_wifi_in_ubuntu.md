---
title: "Help how do I get wifi in ubuntu"
date: 2015-11-28
forum: Networking &amp; Wireless
---

### Post by Simon_Frat on 2015-11-28
Someone I need help how do I get the wifi drivers for ubuntu, my wifi card is a D link N150 pci adapter.

---

### Post by praseodym on 2015-11-28
Hi,

lets get more info about the chipset. Please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```
uname -a
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```
Can you connect via cable?

---

### Post by Simon_Frat on 2015-11-28
I don't have ubuntu right now

It's for future reference

Yes I can via cable I have done it in the past

---

### Post by Bucky Ball on 2015-11-28
Welcome. Perhaps you should revisit this when you have Ubuntu installed and actually have an issue. :D

Bit hard to help with a hypothetical problem.

---

### Post by Simon_Frat on 2015-11-28
I just need too find drivers

---

### Post by Hadaka on 2015-11-28
Here ya go...real drivers for a not yet real system
[http://ubuntuforums.org/showthread.php?t=2271474](http://ubuntuforums.org/showthread.php?t=2271474)
Post #4
Please mark this thread solved by clicking tools
then solved
thanks.

---

### Post by jeremy31 on 2015-11-28
Actually if you have Windows, go into Control Panel/Device Manager then click on Network Adapters you should then see the network adapters, right click on the wireless adapter, then properties and detail tab and from the dropdown box select hardware IDs and post it.  Then we can see if there is a kernel module for your wifi[ATTACH=CONFIG]265806[/ATTACH]

---

### Post by Bucky Ball on 2015-11-28
> **jeremy31 said:**
> Then we can see if there is a kernel module for your wifi[ATTACH=CONFIG]265806[/ATTACH]

There is and Hadaka has linked to full instructions on how to get them and install them.

---

