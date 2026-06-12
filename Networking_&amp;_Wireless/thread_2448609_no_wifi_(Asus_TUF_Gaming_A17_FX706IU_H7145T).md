---
title: "no wifi (Asus TUF Gaming A17 FX706IU H7145T)"
date: 2020-08-10
forum: Networking &amp; Wireless
---

### Post by fredy50 on 2020-08-10
Hello,

i try to create dual boot (Windows and ubuntu)
But then i try to install ubuntu 16.04 i can install the OS but i can't access the WIFI.

But then i try to install ubuntu 20.04 i can see the WIFI but then i install the OS no boot screen just black screen.

Inside the OS ubuntu 16.04.

i got this hardware.
```
fredy@fredy-TUF-Gaming-FA706IU-FX706IU:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1630
00:01.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1632
00:01.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1633
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1632
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1634
00:02.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1634
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1634
00:08.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1632
00:08.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1635
00:08.2 PCI bridge: Advanced Micro Devices, Inc. [AMD] Device 1635
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 51)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 51)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1448
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 1449
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144a
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144b
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144c
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144d
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144e
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Device 144f
01:00.0 VGA compatible controller: NVIDIA Corporation Device 2191 (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 1aeb (rev a1)
01:00.2 USB controller: NVIDIA Corporation Device 1aec (rev a1)
01:00.3 Serial bus controller [0c80]: NVIDIA Corporation Device 1aed (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c822
04:00.0 Non-Volatile memory controller: Kingston Technology Company, Inc. Device 500c (rev 01)
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Device 1636 (rev f0)
05:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 1637
05:00.2 Encryption controller: Advanced Micro Devices, Inc. [AMD] Device 15df
05:00.3 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1639
05:00.4 USB controller: Advanced Micro Devices, Inc. [AMD] Device 1639
05:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Device 15e2 (rev 01)
05:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Device 15e3
06:00.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 81)
```

How can i install wifi driver on ubuntu 16.04 ??? have any idea how to install it ? just be fine if ubuntu 20.04 :)

Thanks for your time !

---

### Post by chili555 on 2020-08-10
> 03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device c822That is your wifi device, but we'd like more precise information about it:

```
lspci -nnk | grep 0280 -A3
```

-------

Note to chili: rtw_8822ce and [https://github.com/lwfinger/rtw88.git](https://github.com/lwfinger/rtw88.git), maybe...

---

### Post by fredy50 on 2020-08-11
here is my out put of the command.

```
fredy@fredy-TUF-Gaming-FA706IU-FX706IU:~$ lspci -nnk | grep 0280 -A3
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:c822]
    Subsystem: AzureWave Device [1a3b:3750]
04:00.0 Non-Volatile memory controller [0108]: Kingston Technology Company, Inc. Device [2646:500c] (rev 01)
    Subsystem: Kingston Technology Company, Inc. Device [2646:500c]
```

can you help me who i can download the driver?

---

### Post by fredy50 on 2020-08-11
then i try to install it you gave me.

```
fredy@fredy-TUF-Gaming-FA706IU-FX706IU:~/wifi/rtw88$ sudo make install
make -C /lib/modules/4.15.0-112-generic/build M=/home/fredy/wifi/rtw88 modules
make[1]: Entering directory '/usr/src/linux-headers-4.15.0-112-generic'
  Building modules, stage 2.
  MODPOST 10 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.15.0-112-generic'
Making backups
tar: /lib/modules/4.15.0-112-generic/kernel/drivers/net/wireless/realtek/rtw88: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
Makefile:83: recipe for target 'install' failed
make: *** [install] Error 2
```

---

### Post by fredy50 on 2020-08-11
got it to work !

Step 1:
sudo apt-get install dkms

Step 2:
wget [https://github.com/juanro49/rtl88x2ce-dkms/releases/download/5.7.3_35403/rtl88x2ce-dkms_35403_amd64.deb](https://github.com/juanro49/rtl88x2ce-dkms/releases/download/5.7.3_35403/rtl88x2ce-dkms_35403_amd64.deb)

Step 3:
sudo dpkg -i rtl88x2ce-dkms_35403_amd64.deb

---

### Post by chili555 on 2020-08-11
> got it to work !Awesome! Glad it's working. Please use thread tools at the top to mark solved. The searchers will appreciate it.

> fredy@fredy-TUF-Gaming-FA706IU-FX706IU:~/wifi/rtw88$ sudo make installI believe there is an error here; however, you've solved it another way.

---

