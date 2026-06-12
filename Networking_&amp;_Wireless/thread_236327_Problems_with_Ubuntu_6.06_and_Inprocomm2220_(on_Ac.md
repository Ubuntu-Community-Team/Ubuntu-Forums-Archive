---
title: "Problems with Ubuntu 6.06 and Inprocomm2220 (on Acer Aspire 1520)"
date: 2006-08-14
forum: Networking &amp; Wireless
---

### Post by Fr4nz on 2006-08-14
Hi guys, I'm a noob and I ask you some patience for my problem.

I've installed Ubuntu 6.06 (for AMD64) on my notebook...all works fine except for the wireless controller! As the topic says, I have an Acer Aspire 1524 with an Inprocomm 2220 wireless controller.

In detail: I've downloaded the 64-bit driver (amdplamet64.com) and ndiswrapper 1.8, I've followed the usual procedure (ndiswrapper -i .... depmod -a ... modprobe ....) and in fact the wireless controller is seen correctly if I write "ifconfig". The problem is that when I try to issue a command to the controller (like "iwlist wlan0 scanning" or "ifconfig wlan0 down" and then "ifconfig wlan0 up") the system hangs up and I have to reboot.

This is really strange because previous versions of ubuntu worked good with my wireless card.

Another thing I've noticed is that when the system boots, the "network configuration .... ok" thing is very very slow to complete, and I have to remove the ndis driver in order to bring back the boot phase at normal speed.

Thanks for any help and excuse me for my bloody english!

Fr4nz

---

### Post by Rincewind on 2006-08-26
Hi Fr4nz,

I've got the same laptop - unfortunately, the 64 bit drivers don't work with ndiswrapper, only the 32 bit ones do.

This is one of the reasons I'm running 32 bit.

I guess the only other option is to buy a supported wifi card.

Rincewind

---

