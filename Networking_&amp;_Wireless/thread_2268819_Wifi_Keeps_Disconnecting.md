---
title: "Wifi Keeps Disconnecting"
date: 2015-03-11
forum: Networking &amp; Wireless
---

### Post by Luis_Figueroa on 2015-03-11
Hello everyone,
I'm new to Linux and i just replaced my Windows 8 OS with Xubuntu 14.10. Everything was going great until I noticed that the Wifi kept disconnecting, but i don't know why. I have perused a good portion of the threads on here to see if i could solve this issue before resorting to posting my own. But alas I have been unsuccessful. I could really use your help. I'm not sure what information you need in order to help me but here's a bit. My laptop is an HP Laptop, Serial # 5CD4469M3H, it is fairly new, having been purchased over this past christmas. I have wifi which worked perfectly when i had windows 8 and which works perfectly on every other device i own, so i know it's not the signal itself. 

Your help is greatly appreciated. :)

---

### Post by ajgreeny on 2015-03-11
Let's see the output in terminal of command ```
lspci -nnk | grep -iA2 net
``` which will show your network hardware chipsets.

---

### Post by Luis_Figueroa on 2015-03-12
Here's the output:

lfigueroa@lfigueroa-HP-15-Notebook-PC:~$ lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter [10ec:8179] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:197d]
	Kernel driver in use: rtl8188ee
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Hewlett-Packard Company Device [103c:8015]
	Kernel driver in use: r8169

---

