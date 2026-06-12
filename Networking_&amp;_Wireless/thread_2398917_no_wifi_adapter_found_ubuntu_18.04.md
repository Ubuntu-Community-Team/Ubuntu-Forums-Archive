---
title: "no wifi adapter found ubuntu 18.04"
date: 2018-08-19
forum: Networking &amp; Wireless
---

### Post by koblla on 2018-08-19
hello
i installed ubuntu 18.04 recently and everything works fine except wifi.
i tried every solution i have seen on this forum none worked, like "sudo apt-get install bcmwl-kernel-source".
i use Lenovo ideapad 320 and my network adapter is RTL8821CE.
please help me
also output for lspci:

```
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 08)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:17.0 SATA controller: Intel Corporation Sunrise Point-LP SATA Controller [AHCI mode] (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port (rev f1)
00:1c.4 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #5 (rev f1)
00:1c.5 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #6 (rev f1)
00:1f.0 ISA bridge: Intel Corporation Device 9d4e (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
00:1f.4 SMBus: Intel Corporation Sunrise Point-LP SMBus (rev 21)
01:00.0 3D controller: NVIDIA Corporation GP108M [GeForce MX150] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
```

output for lsusb:
```
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 5986:210f Acer, Inc 
Bus 001 Device 003: ID 0bda:c024 Realtek Semiconductor Corp. 
Bus 001 Device 008: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by jeremy31 on 2018-08-19
See the wireless script link in my signature and post results

---

### Post by koblla on 2018-08-19
here is my ubuntu pastebin
[http://paste.ubuntu.com/p/mWdXzGJRkC/](http://paste.ubuntu.com/p/mWdXzGJRkC/)

---

### Post by praseodym on 2018-08-19
> ```
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8821CE 802.11ac PCIe Wireless Network Adapter
```
There it is. Driver installation

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
Reboot and deactivate SecureBoot

---

### Post by koblla on 2018-08-19
how to deactivate secureboot ? (im new to ubuntu)

---

### Post by jeremy31 on 2018-08-19
Secure Boot is a setting in UEFI/BIOS

---

### Post by tejaslok on 2018-10-14
> **praseodym said:**
> There it is. Driver installation

```
sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone https://github.com/tomaspinho/rtl8821ce
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh 
```
Reboot and deactivate SecureBoot

Thanks, This worked for me 
Laptop - HP 15g-dr0006tx model.

---

### Post by timlawson4jc on 2018-11-12
I did this in Ubunto 18.1 on a new HP laptop 17-ca0044cl purchased at Costco in 2018. It worked! Thank you,,thank you,,thank you

---

### Post by wisjim2 on 2019-01-21
I've been fighting this problem for months. THANK YOU praseodym!!! This worked like a charm.
[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=1411497")

---

### Post by mando774 on 2019-06-14
you are a god send! I salute you, I've spent so long trying different fixes for this!

---

### Post by gvimbai2000 on 2019-06-17
This worked for me. I'm using an HP 14-ck0xxx. Thanks.
Just one thing though; has anyone noticed how fast the battery drains? My battery is supposed to last 12 hours, but  is only doing about 7 hours now. Could this driver be the reason? Maybe the driver needs to be optimised... but I'm still thankful my wifi works. :)

---

### Post by ibkhayyat on 2019-10-01
Greeting,
HP DW001NJ, with realtek 8821ce wifi adapter here
I found this video that worked for me
[https://www.youtube.com/watch?v=vPfLVsyQU_A](https://www.youtube.com/watch?v=vPfLVsyQU_A)

Cheers

---

### Post by kurt18947 on 2019-10-01
> **gvimbai2000 said:**
> This worked for me. I'm using an HP 14-ck0xxx. Thanks.
Just one thing though; has anyone noticed how fast the battery drains? My battery is supposed to last 12 hours, but  is only doing about 7 hours now. Could this driver be the reason? Maybe the driver needs to be optimised... but I'm still thankful my wifi works. :)

Re fast  battery drain, have you installed TLP? Found in the repositories. It seemed to help my Thinkpad's battery life. Here are details, I didn't do any tweaking, I might do better yet but I'm getting 5+ hours and that has proven more than adequate for my purposes.

[https://wiki.archlinux.org/index.php/TLP](https://wiki.archlinux.org/index.php/TLP)

---

