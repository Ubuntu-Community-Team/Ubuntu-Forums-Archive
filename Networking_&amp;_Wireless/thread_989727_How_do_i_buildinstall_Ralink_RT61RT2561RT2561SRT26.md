---
title: "How do i build/install Ralink RT61:RT2561/RT2561S/RT2661) linux driver in Ubuntu?"
date: 2008-11-21
forum: Networking &amp; Wireless
---

### Post by TJX09 on 2008-11-21
I'm new to Ubuntu Intrepid and I have a wireles 802.11g pci card that have Ralink RT2561/RT61 chipset.The Linux drivers RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)  07/23/2008	1.1.2.2	 is avalaible in Ralink website
for download but i have no clue on how to install it, if anyone has installed the RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661) Linux driver in Ubuntu please share it. How do i build/install Ralink RT61:RT2561/RT2561S/RT2661) linux driver in Ubuntu? 



[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
RT2501PCI/mPCI/CB(RT61:RT2561/RT2561S/RT2661)    07/23/2008	1.1.2.2

---

### Post by iponeverything on 2008-11-21
The rt drivers are in 2.6.27

see if rt61pci loaded.

---

### Post by TJX09 on 2008-11-22
> **iponeverything said:**
> The rt drivers are in 2.6.27

see if rt61pci loaded.

How do i find out if rt61pci is loaded?

---

### Post by iponeverything on 2008-11-22
```
lsmod |grep rt61
```

If you don't see it try:

```
modprobe rt61pci
```

After you do the modprobe post the output of

```
dmesg
```

if you can.

---

