---
title: "ACER wireless problem"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by drumanart on 2008-05-26
Hi folks.
I try to make the wireless connection on my **ACER 5220** laptop to work.
For this I installed **ndiswrapper 1.52** and the driver **bcmwl5** (someone recommanded this driver).


martin@martin-laptop:~$ **ndiswrapper -v**
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.24-16-rt/ubuntu/misc/ndiswrapper/ndiswrapper.ko
version:        1.52
vermagic:       2.6.24-16-rt SMP preempt mod_unload 586 
martin@martin-laptop:~$ 


martin@martin-laptop:~$ **ndiswrapper -l** 
bcmwl5 : driver installed 
martin@martin-laptop:~$ 

martin@martin-laptop:~$ **iwconfig** 
lo        no wireless extensions. 

eth0      no wireless extensions. 

irda0     no wireless extensions. 

I would be very pleased for help

Thks

---

### Post by mapes12 on 2008-05-26
Have you had a go at this HOWTO:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

### Post by gmclachl on 2008-05-26
I don't know if it will help you, but I have an Acer 7520. My output of my lspci shows

 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)


If you have the same on you can install a snapshot of the madwifi drivers and that will get you up and running.

George

---

### Post by mavi_yelkenler on 2008-05-26
hi ,

try that driver -->> [http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-nr-r3366+ar5007.tar.gz)

sudo make
sudo make install
sudo modprobe ath_pci

if you use 7.10 "blacklist ath5k"

be sure build-essentials installed

regards

---

### Post by mavi_yelkenler on 2008-05-26
drumanart sorry. i thought you have an Atheros chipset

---

