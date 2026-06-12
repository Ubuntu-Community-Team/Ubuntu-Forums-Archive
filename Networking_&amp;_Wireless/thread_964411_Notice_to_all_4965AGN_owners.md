---
title: "Notice to all 4965AGN owners"
date: 2008-10-30
forum: Networking &amp; Wireless
---

### Post by damis648 on 2008-10-30
Hello, I though I would point out a major bug with the shipped kernel driver for the Intel 4965AGN wireless card in Intrepid. This bug will cause random kernel panics when you are connected to a wireless N network (not even necessarily high traffic, and can also happen when not connected). It can be hard to narrow down kernel panics, but if you have an Intel 4965AGN card, try the following:
Installing Intrepid cleanly will probably be impossible because you will get kernel panics during the installation. To prevent this, turn the wireless switch off when booting the LiveCD to install 8.10. After installed, connect to a wired network and install the backports package for your kernel (probably will want the linux-backports-modules-intrepid-generic meta package) and reboot. I though people should know this bug before freaking out (like I did).

A launchpad bug report can be found here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)

Hope I can have helped!

PS. Would it be possible to get a sticky on this? I think it's a pretty major bug...

---

