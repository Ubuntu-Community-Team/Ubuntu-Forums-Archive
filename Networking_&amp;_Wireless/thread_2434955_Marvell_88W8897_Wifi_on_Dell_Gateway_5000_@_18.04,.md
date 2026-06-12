---
title: "Marvell 88W8897 Wifi on Dell Gateway 5000 @ 18.04, firmware problem"
date: 2020-01-14
forum: Networking &amp; Wireless
---

### Post by kszonek on 2020-01-14
Got stucked with wireless on industrial PC from Dell. Works great on stock windows, is supposed to run well with ubuntu: [certified hardware]("https://certification.ubuntu.com/hardware/201603-21474")

I am running fresh install of Ubuntu server 18.04.3

$ dmesg | grep mwifiex_pcie
```
[    8.982549] mwifiex_pcie 0000:03:00.0: enabling device (0000 -> 0002)
[    8.982726] mwifiex_pcie: try set_consistent_dma_mask(32)
[    8.982786] mwifiex_pcie: PCI memory map Virt0:         (ptrval) PCI memory map Virt2:         (ptrval)
[    9.116084] mwifiex_pcie 0000:03:00.0: PCI-E is not the winner <0x6>
[    9.116088] mwifiex_pcie 0000:03:00.0: WLAN is not the winner! Skip FW dnld
[   25.336455] mwifiex_pcie 0000:03:00.0: FW failed to be active in time
[   25.336460] mwifiex_pcie 0000:03:00.0: info: _mwifiex_fw_dpc: unregister device
```

$ lspci | grep net
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 19)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 19)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88W8897 [AVASTAR] 802.11ac Wireless
```

$ uname -a
```
Linux 4.15.0-74-generic #84-Ubuntu SMP Thu Dec 19 08:06:28 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux
```

ip / ifconfig / iwconfig show no wireless interface at all.

I am experienced with Linux, but cant move any forward, any hint? Maybe just point me in the right direction... Already spend few days on it and no progress.

edit:
$ ls /lib/firmware/mrvl
```
pcie8897_uapsta.bin        pcieusb8997_combo_v4.bin  sd8787_uapsta.bin  sd8887_uapsta.bin   usb8797_uapsta.bin  usbusb8997_combo_v4.bin
pcie8997_wlan_v4.bin       sd8688.bin                sd8797_uapsta.bin  sd8897_uapsta.bin   usb8801_uapsta.bin
pcieuart8997_combo_v4.bin  sd8688_helper.bin         sd8801_uapsta.bin  usb8766_uapsta.bin  usb8897_uapsta.bin
```

---

### Post by CelticWarrior on 2020-01-14
Disable Secure Boot and try again.

---

### Post by chili555 on 2020-01-14
May we see:```

ls -al /lib/firmware/mwlwifi
```

---

### Post by kszonek on 2020-01-15
Tried disabling Secure Boot - no change.

$ ls -al /lib/firmware/mwlwifi
```
total 620
drwxr-xr-x  2 root root   4096 Jan 13 11:00 .
drwxr-xr-x 84 root root  20480 Jan 13 11:01 ..
-rw-r--r--  1 root root 116356 Nov 17  2017 88W8864.bin
-rw-r--r--  1 root root 489084 Nov 17  2017 88W8897.bin
```

---

### Post by soundmixermike on 2020-01-20
I'm using Peppermint #28~18.04.1-Ubuntu on a Surface 3 with the same wifi controller. My experience is that if I turn off power management it will work for some time however, it will eventually it'll still disappear but there is no predictable time when that will happen. I'm happy to help with some guidence.

---

### Post by kszonek on 2020-01-22
@soundmixermike

You are one step further than me - I can't even get interface to show up, not to mention get connection going. Did you do anything in particular to get there?

I bough Dell Gateway with Linux preinstalled (previous one was shipped with Windows 10 Pro). Default Linux setup is running Ubuntu Core 15 and WiFi works on it (at least interface shows up with `ip a` and `iwconfig`). Unfortunately Core 16 wont work for me for several reasons, so I need to figure out how to get it going on 16.04.

On Core15:
$ ls -l /lib/firmware/mrvl/
```
-rw-r--r-- 1 root root 689624 Jan  6  2016 pcie8897_uapsta.bin
-rw-r--r-- 1 root root 259172 Dec  1  2014 sd8688.bin
-rw-r--r-- 1 root root   2616 Dec  1  2014 sd8688_helper.bin
-rw-r--r-- 1 root root 463240 Nov 20  2015 sd8787_uapsta.bin
-rw-r--r-- 1 root root 458108 Dec  1  2014 sd8797_uapsta.bin
-rw-r--r-- 1 root root 391772 Nov 20  2015 sd8887_uapsta.bin
-rw-r--r-- 1 root root 734612 Nov 20  2015 sd8897_uapsta.bin
-rw-r--r-- 1 root root 478836 Nov 20  2015 usb8766_uapsta.bin
-rw-r--r-- 1 root root 551720 Nov 20  2015 usb8797_uapsta.bin
-rw-r--r-- 1 root root 752340 Nov 20  2015 usb8897_uapsta.bin
```

$ ls -l /lib/firmware/mwlwifi
```
ls: cannot access /lib/firmware/mwlwifi: No such file or directory
```

$ dmesg | grep mwi
```
[   10.203878] mwifiex_pcie 0000:03:00.0: enabling device (0000 -> 0002)
[   10.204183] mwifiex: rx work enabled, cpus 2
[   10.335596] mwifiex_pcie 0000:03:00.0: PCI-E is the winner
[   12.126222] mwifiex_pcie 0000:03:00.0: WLAN FW is active
[   12.265954] mwifiex_pcie 0000:03:00.0: driver_version = mwifiex 1.0 (15.150.13.p21)
```

edit:

$ rm /lib/firmware/mrvl/* && rm /lib/firmware/mwlwifi/*
$ modprobe -r mwifiex_pcie && modpribe mwifiex_pcie
$ dmesg
```
[ 1589.305861] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[ 1589.306572] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[ 1589.326429] mwifiex_pcie: try set_consistent_dma_mask(32)
[ 1589.326510] mwifiex_pcie: PCI memory map Virt0: 0000000020fc1553 PCI memory map Virt2: 00000000685da724
[ 1589.332075] mwifiex_pcie 0000:03:00.0: Direct firmware load for mrvl/pcie8897_uapsta.bin failed with error -2
[ 1589.332161] mwifiex_pcie 0000:03:00.0: Failed to get firmware mrvl/pcie8897_uapsta.bin
[ 1589.332164] mwifiex_pcie 0000:03:00.0: info: _mwifiex_fw_dpc: unregister device
```

Restoring *mrvl/pcie8897_uapsta.bin* from Core15 mkes no change, error message still:
```
[ 1557.139513] cfg80211: Loading compiled-in X.509 certificates for regulatory database
[ 1557.140231] cfg80211: Loaded X.509 cert 'sforshee: 00b28ddf47aef9cea7'
[ 1557.161673] mwifiex_pcie: try set_consistent_dma_mask(32)
[ 1557.161766] mwifiex_pcie: PCI memory map Virt0: 0000000020fc1553 PCI memory map Virt2: 00000000685da724
[ 1557.269659] mwifiex_pcie 0000:03:00.0: PCI-E is not the winner <0x6>
[ 1557.269672] mwifiex_pcie 0000:03:00.0: WLAN is not the winner! Skip FW dnld
```

Firmware files were different before swap.

Something got broken at some point, but it seems not the firmware file.... no idea where to go now. Hints?

---

