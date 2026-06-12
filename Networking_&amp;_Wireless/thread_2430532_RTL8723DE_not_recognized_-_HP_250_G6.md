---
title: "RTL8723DE not recognized - HP 250 G6"
date: 2019-11-03
forum: Networking &amp; Wireless
---

### Post by emzu on 2019-11-03
Hi all!

my wifi card RTL8723DE is not recognized. 
Attached the wifi.txt info.

Thank you for your support!!

---

### Post by chili555 on 2019-11-03
Please check here: [https://askubuntu.com/questions/1047245/wifi-adapter-not-found-in-ubuntu-18-04/1050793#1050793](https://askubuntu.com/questions/1047245/wifi-adapter-not-found-in-ubuntu-18-04/1050793#1050793)

You probably don't need all this stuff that is, frankly, unrelated:

> sudo apt purge bcmwl-kernel-source
sudo sed -i '/blacklist bcma/ d' /etc/modprobe.d/blacklist.conf
sudo sed -i '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.confYou will also need to disable Secure Boot in the BIOS/EFI.

---

### Post by emzu on 2019-11-03
It worked! 

Thanks a lot!

---

### Post by mörgæs on 2019-11-03
Good, please mark the thread solved.

---

