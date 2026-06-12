---
title: "Miss ath0 after upgrading kernel"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by eddyxu on 2006-12-20
I use xubuntu, and today morning I just upgrade my kernel from 2.6.19 to 2.6.20.

In the first, I found the wireless dosen't work. So I thought it could be reinstall a wireless card driver for new kernel. So I use :

sudo ndiswrapper -i foo.inf
sudo depmod -a
sudo modprobe ndiswrapper

But the progress hanged in "modprobe ndiswrapper" for minites, I reboot the machine and go back to 2.6.19, but when i input "ifconfig" i can't see "ath0" . Then i reinstall the driver just like above. No error message printed, but i still can't see ”aht0" after "modprobe ndiswrapper"

Why?

---

### Post by eddyxu on 2006-12-22
Does anyone meet this problem in feisty?

---

