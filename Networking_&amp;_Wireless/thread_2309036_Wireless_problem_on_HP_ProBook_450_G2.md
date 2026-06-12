---
title: "Wireless problem on HP ProBook 450 G2"
date: 2016-01-07
forum: Networking &amp; Wireless
---

### Post by Huy_Tu on 2016-01-07
I have a HP ProBook 450 G2 notebook with pre-installed  Windows 10, I have set up the newest Ubuntu dualboot with Windows on it.  But I have a problem with unstable Wireless on Ubuntu. Wireless only  work for over first 10 minutes, after that wifi disconect and I cannt  connect to any wireless network then. I cannt know how to solve it.  I have try other distro and i have some problem on them. anyone  can help me solve this problem? Sorry for bad English  ;)

---

### Post by janmes2 on 2016-02-23
Try adding the words "iommu=soft" at the grub menu before you boot.

If it works, add it permanently as follows;

run the following command: sudo gedit /etc/default/grub


Edit the empty quotes in this line to read: GRUB_CMDLINE_LINUX="iommu=soft"


save changes to grub and exit gedit and the terminal


Open up a new terminal with ctrl+alt+t 


run the following command: sudo update-grub


then exit the terminal using this command: exit


Restart your computer

---

