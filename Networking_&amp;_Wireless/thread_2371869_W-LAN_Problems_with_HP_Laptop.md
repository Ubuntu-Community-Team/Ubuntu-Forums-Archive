---
title: "W-LAN Problems with HP Laptop"
date: 2017-09-19
forum: Networking &amp; Wireless
---

### Post by marcok2 on 2017-09-19
Hello Guys,
I have a problem, i have installed Ubuntu on my new Laptop, the HP 250 G6. I know for sure that it has a wireless card in it, but it has "vanished", i can't see it inside my system. I have tried some things, and i am pretty sure it is attached as a USB Device, which i do not understand.

```
lsusb:

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04f2:b5db Chicony Electronics Co., Ltd 
**Bus 001 Device 003: ID 0bda:b009 Realtek Semiconductor Corp. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
sudo lshw -short

H/W path       Device      Class          Description
=====================================================
                           system         HP 250 G6 Notebook PC (1WY81EA#UUZ)
/0                         bus            832A
/0/0                       memory         128KiB BIOS
/0/4                       processor      Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz
/0/4/5                     memory         128KiB L1 cache
/0/4/6                     memory         512KiB L2 cache
/0/4/7                     memory         3MiB L3 cache
/0/26                      memory         8GiB System Memory
/0/26/0                    memory         8GiB SODIMM Synchronous 2133 MHz (0.5 ns)
/0/26/1                    memory         SODIMM DDR Synchronous [empty]
/0/100                     bridge         Intel Corporation
/0/100/2                   display        Intel Corporation
/0/100/4                   generic        Intel Corporation
/0/100/8                   generic        Sky Lake Gaussian Mixture Model
/0/100/14                  bus            Intel Corporation
/0/100/14/0    usb1        bus            xHCI Host Controller
/0/100/14/0/4              communication  802.11n WLAN Adapter
/0/100/14/0/5              multimedia     HP Webcam
/0/100/14/1    usb2        bus            xHCI Host Controller
/0/100/14.2                generic        Intel Corporation
/0/100/16                  communication  Intel Corporation
/0/100/17                  storage        Intel Corporation
/0/100/1c                  bridge         Intel Corporation
/0/100/1c/0    eno1        network        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
/0/100/1c.5                bridge         Intel Corporation
/0/100/1c.5/0              network        Realtek Semiconductor Co., Ltd.
/0/100/1f                  bridge         Intel Corporation
/0/100/1f.2                memory         Memory controller
/0/100/1f.3                multimedia     Intel Corporation
/0/100/1f.4                bus            Intel Corporation
/0/1           scsi0       storage        
/0/1/0.0.0     /dev/sda    disk           256GB SAMSUNG MZNLN256
/0/1/0.0.0/1               volume         511MiB Windows FAT volume
/0/1/0.0.0/2   /dev/sda2   volume         230GiB EXT4 volume
/0/1/0.0.0/3   /dev/sda3   volume         8107MiB Linux swap volume
/0/2           scsi1       storage        
/0/2/0.0.0     /dev/cdrom  disk           DVDRW  DA8AESH
/1                         power          JC03031
/2                         power          OEM Define 5


```

I have no idea what i have to do, or what info i should give you, i'm really sorry.

Thanks in advance

Marcok

---

### Post by jeremy31 on 2017-10-23
See the wireless script link in my signature and post results

---

