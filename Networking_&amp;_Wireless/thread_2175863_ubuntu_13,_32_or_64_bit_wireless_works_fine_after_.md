---
title: "ubuntu 13, 32 or 64 bit: wireless works fine after instalation but after reboot..."
date: 2013-09-21
forum: Networking &amp; Wireless
---

### Post by AlexBill on 2013-09-21
Hi all
Yesterday I installed ubuntu 13 64 bit on portege 930. After installation everything works fine, including internet access via wireless. I rebooted computer and enter again in ubuntu, wireless connects well but then I have no access to internet. not ping to local gateway or too slow.
then I removed 64 bit version and installed 32  bit version of ubuntu 13. everything worked fne and I turned off computer. Today I stated it again , network connection is stablished but no internet access again. How sad... I run script to grag networj info and is on attachment. I also attached a file with gateway ping info. Lots of packed loss.
In windows 7, everything is fine.
Thanks a lot

Alex

---

### Post by Hadaka on 2013-09-21
Hi,check your router settings and set for wap2 or wep NO TKIP.
then do..
```
sudo modprobe -r iwlwifi
sudo modprobe -v iwlwifi 11n_disable=1
```
dont boot.
If that works,we can write a file to make it permanent.
thanks.

---

### Post by praseodym on 2013-09-22
Additionally, deactivate the power management:
```

sudo iwconfig wlan0 power off
```

---

