---
title: "No BCM in lspci"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by prove-test on 2007-11-08
Hi at all,
yesterday i've got that strange problem.
I've got a HP Pavillion dv9000 with broadcom wireless card.
I've got gusty gibbons since 1 week and i use my wireless connection without any problem.
Yesterday when i boot my laptop, without making change in kernel image or kernel modules, my eth1 (wifi interfaces) do not list in iwlist scan.
So i'll make lspci and there is no Broadcom output like 1 day ago.
I use ndiswrapper driver so i'll try to use bcm43xx kernel module insted of that but nothing change.
The wrong think are that if i boot with kubuntu live cd in lspci i've got an output for broadcom card.
Any suggestion?
tnx in advance

---

### Post by prove-test on 2007-11-09
I'm going crazy!
tomorrow i'll power on my pc and the wifi eth work good!
in lspci i have:
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
?!?!?!?!?!?!?!?
magic?

---

