---
title: "eth1 disappeared after updates from ubuntu-proposed"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by ernstblaauw on 2008-11-26
I'm running Intrepid. Yesterday, I installed the linux-backports-modules-intrepid package. After that, I was not able to connect to wireless networks.
Today, I found this bugreport: [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/287450](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-2.6.27/+bug/287450)
There was a bug in the package I installed and the fix was in ubuntu-proposed. So, I enabled ubuntu-proposed and updated. After installing 123 packages and rebooting, my wireless interface eth1 disappeared:
- no wireless networks with NetworkManager
- system > administration > network tools do not show interface eth1
lspci shows:
```
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```
Does anyone know how to get back my eth1?

---

### Post by ernstblaauw on 2008-11-26
Removing the packages by doing 'sudo apt-get remove linux-backports-modules-*' solved the problem (but I do not have the backported drivers available). Does anyone has a solution where the packages stay installed?

Update:
I filled in a bug report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/302417](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/302417)
I do not think it is necessary to continue here.

---

