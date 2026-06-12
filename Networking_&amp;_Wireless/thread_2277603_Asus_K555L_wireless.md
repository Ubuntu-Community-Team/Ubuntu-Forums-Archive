---
title: "Asus K555L wireless"
date: 2015-05-10
forum: Networking &amp; Wireless
---

### Post by Gabriel_Cristache on 2015-05-10
I have recently purchased an Asus K555L and I cannot make the wireless to work on an Ubuntu 14.04LTS. First of all I do not even have the "Enable Wireless" option on the wireless icon in the upper right corner. I have looked it up on the internet but I couldn't find anything. 
Any help would be appreciated.

---

### Post by dino99 on 2015-05-10
with a recent hardware, also install the most recent kernel to get a better chance to use that wireless chipset

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.2-wily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0.2-wily/)
download the 4 packages (2 headers + 2 images) into an empty folder, then>  sudo dpkg -i *

---

### Post by jeremy31 on 2015-05-10
> **Gabriel_Cristache said:**
> I have recently purchased an Asus K555L and I cannot make the wireless to work on an Ubuntu 14.04LTS. First of all I do not even have the "Enable Wireless" option on the wireless icon in the upper right corner. I have looked it up on the internet but I couldn't find anything. 
Any help would be appreciated.

Please post the result of ```
lshw -c net; lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by rogant on 2015-10-28
Hello

I have the same problem, jeremy31 thats is my output

```
rogant@avargas-vpc:~$ lshw -c net; lspci -nnk | grep -iA2 net; rfkill list allWARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 1c:b7:2c:87:0e:c8
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.60.109 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:48 ioport:e000(size=256) memory:f7204000-f7204fff memory:f7200000-f7203fff
  *-network UNCLAIMED
       description: Network controller
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f7100000-f71fffff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:200f]
    Kernel driver in use: r8169
03:00.0 Network controller [0280]: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter [14c3:7630]
    Subsystem: Foxconn International, Inc. Device [105b:e084]
04:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1347] (rev a2)
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no



```

---

### Post by slickymaster on 2015-10-28
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by praseodym on 2015-10-28
Try this driver via cable connection:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms git
git clone https://github.com/neurobin/MT7630E/
cd MT7630E/
make
sudo make install
```

---

