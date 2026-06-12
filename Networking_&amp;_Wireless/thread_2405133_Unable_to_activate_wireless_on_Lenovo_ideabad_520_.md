---
title: "Unable to activate wireless on Lenovo ideabad 520 (Device c821) ubuntu 16.04"
date: 2018-11-01
forum: Networking &amp; Wireless
---

### Post by mohmedelwany on 2018-11-01
I tried a lot before reaching to this reply
So may I damaged something in the system 

"[COLOR=#242729][FONT=Arial](Requirements: **kernel >=4.11**) :[/FONT][/COLOR]


[LIST=1]
[*]Download driver directory from this repo:[https://github.com/endlessm/linux/tr...less/rtl8821ce]("https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce"). You can do it by this link: [https://minhaskamal.github.io/DownGi...less/rtl8821ce]("https://minhaskamal.github.io/DownGit/#/home?url=https://github.com/endlessm/linux/tree/master/drivers/net/wireless/rtl8821ce") 
[*]Unpack zip archive. 
[*]Change the **Makefile**. Line "export TopDIR ?= ..." to export "TopDIR ?= PATH TO EXTRACTED DIRECTORY". 
[*]make 
[*]sudo make install 
[*]sudo modprobe -a 8821ce" 
[/LIST]
[https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710](https://ubuntuforums.org/showthread.php?t=2371149&page=3&p=13702710#post13702710)

no changes happened after I made that




[B]lspci:
[/B]```
00:00.0 Host bridge: Intel Corporation Device 5914 (rev 08)
00:02.0 VGA compatible controller: Intel Corporation Device 5917 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Device 9d10 (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Device 9d71 (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation Device 1d10 (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c821

```ls /etc/modprobe.d/:
```

alsa-base.conf                  blacklist.conf.dpkg-dist    blacklist-rare-network.conf     libopenni-sensor-pointclouds0.conf
amd64-microcode-blacklist.conf  blacklist-firewire.conf     blacklist-watchdog.conf         mlx4.conf
backports.conf                  blacklist-framebuffer.conf  dkms.conf                       nvidia-384_hybrid.conf
blacklist-ath_pci.conf          blacklist-ideapad.conf      fbdev-blacklist.conf            nvidia-graphics-drivers.conf
blacklist-bcm43.conf            blacklist-modem.conf        ideapad.conf                    vmwgfx-fbdev.conf
blacklist.conf                  blacklist-oss.conf          intel-microcode-blacklist.conf

```

uname -r:
```

4.15.0-38-generic

```

iwconfig :
```

lo        no wireless extensions.


enp2s0    no wireless extensions.


enp0s20f0u3  no wireless extensions.

```

---

### Post by mohmedelwany on 2018-11-05
Sorry for putting it in the wrong category

Can any one help me ?

---

### Post by praseodym on 2018-11-05
This one is better

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
Reboot and deactivate SecureBoot.

First uninstall the other one and delete that folder
```

make clean
make
sudo make uninstall
```

---

### Post by mohmedelwany on 2018-11-05
> **praseodym said:**
> This one is better

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
Reboot and deactivate SecureBoot.

First uninstall the other one and delete that folder
```

make clean
make
sudo make uninstall
```


Thank you for your reply 

unfortunately still nothing change 
I couldn't find Secureboot in the bios like other laptops
I read if it's activated, it prevents laptop from booting by external device --> I don't have this problem

---

### Post by mohmedelwany on 2018-11-16
Thank you my friend
after I gave up 
suddenly it works
I'm not sure what made it work
but
before it works 

I made all of that
sudo modprobe -a 8821ce



I followed this link
[https://www.rosehosting.com/blog/how-to-fix-broken-packages-on-ubuntu-16-04-and-debian-9/](https://www.rosehosting.com/blog/how-to-fix-broken-packages-on-ubuntu-16-04-and-debian-9/)

To fix errors in ubuntu

and made
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

and the next day It works :D

---

### Post by LilianaMx on 2018-11-16
I have two days trying to make work again my wifi, could anyone guide me?

Here's my info:
[http://paste.ubuntu.com/p/RXG3zdfcpR/](http://paste.ubuntu.com/p/RXG3zdfcpR/)

---

### Post by wildmanne39 on 2018-11-16
Hello LilianaMx, please start your own thread instead of posting in someone else's so you can get the help you need and so can the OP of this thread.

Thanks

---

