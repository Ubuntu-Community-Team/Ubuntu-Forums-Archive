---
title: "Ethernet card not detected"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by jchenzhao on 2005-05-28
Hi, there,

I am a linux newbie...

I installed Ubuntu onto Dell Latitude 610. **During installation, the network part was skipped **because there was no (wireless/ethernet) connection at that time. Later afer the installation, with the ethernet cable wired, I booted to Ubuntu. However, the **ethernet card is not detected**. I notice if I reinstall Ubuntu with the computer wired up, The problem may gone. However, **is there a quicker way to fix the prolem**?

Thanks in advance!

---

### Post by thrift on 2005-05-28
If you could please identify exactly what models of ethernet/wireless cards you are try to install it would be really helpfull.  

If you run these two commands in a terminal and attach the files lspci.txt and dmesg.txt in your home directory it will help even more.  Please run these commands with all the hardware you are trying to configure in the machine.

dmesg > dmesg.txt
lspci > lspci.txt

If your wired ethernet card is picking up during install, but not after a previous install that took place without the card in, it should be trivial to get it to work without reinstalling.

---

### Post by jchenzhao on 2005-05-29
Thanks thrift for your suggestion.

However, the problem may be due to the ethernet card (Broadcom Netxtreme 57xx driver)? because I googled the web and seems other guys had the same problem with this driver. I had wireless problem as well due to the wireless card ( Dell wireless 1370 miniPCI ) :(

So far I really cannot say I am lucky in my Ubuntu journey.

---

### Post by jchenzhao on 2005-05-29
[QUOTE=thrift]If you could please identify exactly what models of ethernet/wireless cards you are try to install it would be really helpfull.  

If you run these two commands in a terminal and attach the files lspci.txt and dmesg.txt in your home directory it will help even more.  Please run these commands with all the hardware you are trying to configure in the machine.

dmesg > dmesg.txt
lspci > lspci.txt

If your wired ethernet card is picking up during install, but not after a previous install that took place without the card in, it should be trivial to get it to work without reinstalling.[/QUOTE]

Thanks thrift...

the wired ethernet works now. I was silly that I did not check "this deice is configured" box in System->Administration->Networking->Ethernet Connection->Property :(.

Thanks any way.

---

