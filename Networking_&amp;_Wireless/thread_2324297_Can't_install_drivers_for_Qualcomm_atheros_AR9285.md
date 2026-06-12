---
title: "Can't install drivers for Qualcomm atheros AR9285"
date: 2016-05-12
forum: Networking &amp; Wireless
---

### Post by Karsza_Levente on 2016-05-12
Hello, I have a Qualcomm atheros AR9285 Network card
I can't install any drivers, I tried everything.
I'M using Ubuntu 16.04 LTS
I can't connect to internet, I installed DKMS.deb and BCMWL-KERNEL-SOURCE.beb from my bootablee USB stick too.

---

### Post by jeremy31 on 2016-05-12
Welcome to the forum.  With Ubuntu 16.04 you should not need to install anything to get the Atheros AR9285 wireless card working as it has been supported by the Linux kernel for some time now using the ath9k module

Can you connect the computer with the problem by ethernet?  If you can, see the wireless script link in my signature and post the results

If you can't connect by ethernet look at ```
rfkill list all
``` If something is hard blocked, you might have a switch on the computer that can enable/disable wireless- usually not a FN + keyboard combo
If you have a soft block using the FN + keyboard combo may enable

Also check ```
lspci -nnk | grep -iA2 net
```
This will show some info about your network cards, under the AR9285, hopefully it shows
```
Kernel driver in use: ath9k
```

Check System Settings. then Network, is a wifi device listed?  Or is there one or 2 ethernet, try ```
systemctl restart NetworkManager.service
``` and see if wifi functions

---

### Post by Karsza_Levente on 2016-05-13
Than you so much, I know I wasn't specific at all, but this heled thank you!

---

