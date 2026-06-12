---
title: "Hp G6060ea"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by mjswanston on 2008-07-12
Hello all, brought myself a HP G6060EA laptop with was preinstalled with Windows Vista immediately formated the partition and loaded it with ubuntu 8 however struggling to get the wireless working.

drivers are install the default ones from ubuntu, however no luck and it is not working. Please advise thanks. MJ Swanston.

if you wish to email directly, its [email]mattmooo@mac.com[/email]

---

### Post by nixscripter on 2008-07-13
What is the wireless card? I assume it's PCI? If you don't know, do in the Terminal: ```
lspci -nn
``` And look for it in the list.

In general, drivers are a difficult thing; many work, but some require external firmware (e.g. Broadcomm) which you have to install yourself. Others do not have a linux driver, but have a Windows driver which can be used with **ndiswrapper**. It depends on the card what should be done next.

---

### Post by mjswanston on 2008-07-14
I am unsure can't find any information and the HP Website is useless for getting the required information when i have looked on the Internet i believe it is Broadcom.

---

### Post by nixscripter on 2008-07-15
In that case, try this command: ```
sudo lshw -C network -businfo
``` You should get something, even if the card itself is not recognized. If you can figure out where it is (what bus and device number), then either the serial number or PCI device number can be looked up with another command. That should identify the card.

---

