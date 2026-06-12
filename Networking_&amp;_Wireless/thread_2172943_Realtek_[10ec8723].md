---
title: "Realtek [10ec:8723]"
date: 2013-09-07
forum: Networking &amp; Wireless
---

### Post by Sam_Wootton on 2013-09-07
Hi,

Thanks for any help.

I am having trouble seeing my wireless card.  Im not sure what my next action should be, im not clear on what the problem is.

Here are the details:

OS: Ubuntu 12.04
[COLOR=#666666][FONT=arial]Wireless card: OcUK Combo Card BT+WLAN 802.11bgn

Here is the output from various commands:

[/FONT][/COLOR][COLOR=#ff0000]***nm-tool***[/COLOR]
NetworkManager Tool
State: disconnected
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        EC:A8:6B:F6:14:B9


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off



[COLOR=#ff0000]***sudo lshw -C network***[/COLOR]
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: ec:a8:6b:f6:14:b9
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k firmware=0.15-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:41 memory:f7d00000-f7d1ffff memory:f7d29000-f7d29fff ioport:f080(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:e000(size=256) memory:f7c00000-f7c03fff




[COLOR=#ff0000]***iwconfig***[/COLOR]
lo        no wireless extensions.
eth0      no wireless extensions.


[COLOR=#ff0000]***sudo lspci -nn***[/COLOR]
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 04)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723]

I found

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I have the [COLOR=#000000][FONT=Arial]802.11 Wireless LAN Solutions:
[/FONT][/COLOR]
[http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions](http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions)

Whats worrying is that when i run "lspci" i dont see my wireless card at all.

Regards, Sam

[COLOR=#666666][FONT=arial]
[/FONT][/COLOR]

---

### Post by Sam_Wootton on 2013-09-07
ok, so i read this post:

[http://askubuntu.com/questions/115293/wireless-card-unseen-by-lspci](http://askubuntu.com/questions/115293/wireless-card-unseen-by-lspci)

and wanted to try to change wireless settings in BIOS, as suggested also here

[http://ubuntuforums.org/showthread.php?t=1803808](http://ubuntuforums.org/showthread.php?t=1803808)

However, I can only see my GUI Intel BIOS, and this has no mention of wireless settings.

Does anyone know how to change (on/off) wireless settings in BIOS?

Regards, Sam

---

### Post by chili555 on 2013-09-07
> Whats worrying is that when i run "lspci" i dont see my wireless card at all.But I do!> Realtek Semiconductor Co., Ltd. Device [[COLOR="#FF0000"]10ec:8723[/COLOR]]If you search this forum for 10ec:8723, you will see many threads on how to install this driver, including some authored by me!

Which 12.04 version do you have? I believe 12.04.3 LTS includes the 3.8.0-29 kernel which includes the driver for the famous 8723 device. You could also certainly upgrade to 13.04.

---

### Post by Sam_Wootton on 2013-09-08
Hi C[COLOR=#000000]hili555,

Thanks for your reply.

I have LTS 12.04.

I spent some time going through 3 pages ofr previous posts, but couldnt really find anything that helped, and still not sure what to do.

Here are some commands i ran

```

 service networking restart
stop: Unknown instance: 
networking stop/waiting


sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter


sudo apt-get install firmware-b43-lpphy-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-lpphy-installer


sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-installer




rfkill list all
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

I am stuck as to what my problem is, and what threads / posts are relevant.  A lot have them marked as "solved", but arent actually solved.

Regards, Sam
[/COLOR]

---

### Post by Sam_Wootton on 2013-09-08
```

uname -a
Linux sam-desktop-server 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

```

```

sam@sam-desktop-server:/etc/modprobe.d$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

```

I want to follow these steps

[http://www.answeredubuntu.com/139632/wireless_card_realtek_rtl8723ae_bt_is_not_recognized#sthash.7PUUzwPK.dpbs](http://www.answeredubuntu.com/139632/wireless_card_realtek_rtl8723ae_bt_is_not_recognized#sthash.7PUUzwPK.dpbs)

but i am unable to run:

```
sudo apt-get install build-essential linux-headers-generic linux-headers-'uname -r'
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential
E: Unable to locate package linux-headers-generic
E: Unable to locate package linux-headers-uname -r
sam@sam-desktop-server:~$ 

```


How / where can i get build-essential linux-headers-generic from, if i dont have an internet connection on my machine?

[http://packages.ubuntu.com/precise-updates/linux-headers-3.5.0-23-generic](http://packages.ubuntu.com/precise-updates/linux-headers-3.5.0-23-generic)

[COLOR=#636363][FONT=Open Sans]

[/FONT][/COLOR]

---

### Post by Sam_Wootton on 2013-09-08
I downloaded

linux-headers-3.5.0-23_3.5.0-23.35~precise1_all

and installed (through GUI) on linux machine.

However, when i attempt to re-run make / make install for driver

8723AE_8723AU_Linux_support_0419.tar

I still get

```

0419$ sudo make
cp -f rlt8723a_chip_b_cut_bt40_fw_asic_rom_patch-svn7125-0x2C1EFF37-20120314-Linux.bin /lib/firmware/rtk8723a
make -C blutooth_usb_driver -s
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_intr_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:122:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_submit_intr_urbâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:161:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_bulk_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:209:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_submit_bulk_urbâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:248:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_isoc_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:294:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_submit_isoc_urbâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:361:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_tx_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:418:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_openâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:465:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_closeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:520:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_flushâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:548:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_send_frameâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:560:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_notifyâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:674:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜__set_isoc_interfaceâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:686:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_probeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:852:6: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:862:6: error: â€˜struct hci_devâ€™ has no member named â€˜destructâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:865:6: error: â€˜struct hci_devâ€™ has no member named â€˜ownerâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_disconnectâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:906:2: error: implicit declaration of function â€˜__hci_dev_holdâ€™ [-Werror=implicit-function-declaration]
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:920:2: error: implicit declaration of function â€˜__hci_dev_putâ€™ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.o] Error 1
make[2]: *** [_module_/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver] Error 2
make[1]: *** [all] Error 2
make: *** [install] Error 2
sam@sam-desktop-server://home/sam/8723AE_8723AU_Linux_support_0419$ sudo make install
cp -f rlt8723a_chip_b_cut_bt40_fw_asic_rom_patch-svn7125-0x2C1EFF37-20120314-Linux.bin /lib/firmware/rtk8723a
make -C blutooth_usb_driver -s
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_intr_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:122:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_submit_intr_urbâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:161:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_bulk_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:209:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_submit_bulk_urbâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:248:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_isoc_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:294:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_submit_isoc_urbâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:361:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_tx_completeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:418:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_openâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:465:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_closeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:520:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_flushâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:548:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_send_frameâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:560:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_notifyâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:674:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜__set_isoc_interfaceâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:686:32: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_probeâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:852:6: error: â€˜struct hci_devâ€™ has no member named â€˜driver_dataâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:862:6: error: â€˜struct hci_devâ€™ has no member named â€˜destructâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:865:6: error: â€˜struct hci_devâ€™ has no member named â€˜ownerâ€™
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c: In function â€˜btusb_disconnectâ€™:
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:906:2: error: implicit declaration of function â€˜__hci_dev_holdâ€™ [-Werror=implicit-function-declaration]
/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.c:920:2: error: implicit declaration of function â€˜__hci_dev_putâ€™ [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors
make[3]: *** [/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver/rtk_btusb.o] Error 1
make[2]: *** [_module_/home/sam/8723AE_8723AU_Linux_support_0419/blutooth_usb_driver] Error 2
make[1]: *** [all] Error 2
make: *** [install] Error 2
sam@sam-desktop-server://home/sam/8723AE_8723AU_Linux_support_0419$ sudo modprobe rtl8723e
FATAL: Module rtl8723e not found.
sam@sam-desktop-server://home/sam/8723AE_8723AU_Linux_support_0419$ 

```

---

### Post by chili555 on 2013-09-08
First, did you also install build-essential and *ALL* its dependencies? Second, where did you get this awful thing?> 8723AE_8723AU_Linux_support_0419And this???> rlt8723a_chip_b_cut_bt40_fw_asic_rom_patch-svn7125-0x2C1EFF37-20120314-Linux.binOh my, oh my! I doubt they are the correct drivers and I doubt they will even work. You didn't find this on the forum, did you?

You could struggle along for days and still not get this thing going or you could simply and quickly:>  I believe 12.04.3 LTS includes the 3.8.0-29 kernel which includes the driver for the famous 8723 device. You could also certainly upgrade to 13.04. [http://packages.ubuntu.com/precise/linux-image-3.8.0-30-generic](http://packages.ubuntu.com/precise/linux-image-3.8.0-30-generic)

---

### Post by Sam_Wootton on 2013-09-08
Chili555,

Thanks for your continued help. 

It seems i am doing lots wrong.  But i don't know where to get correct packages or drivers, or what order i should be doing this in?  I don't have any connection on my Ubuntu box, so I have to download stuff separately and put it on usb.

I got packages from

[http://packages.ubuntu.com/precise-updates/linux-headers-3.5.0-23-generic](http://packages.ubuntu.com/precise-updates/linux-headers-3.5.0-23-generic)

and was trying to follow

[http://www.answeredubuntu.com/139632/wireless_card_realtek_rtl8723ae_bt_is_not_recognized#sthash.7PUUzwPK.dpbs](http://www.answeredubuntu.com/139632/wireless_card_realtek_rtl8723ae_bt_is_not_recognized#sthash.7PUUzwPK.dpbs)

and/or

[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/154935#154935](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized/154935#154935)

Regards, Sam

---

### Post by chili555 on 2013-09-08
In order to get this to work the way you are going, you need linux-headers, build-essential, dpkg-dev, fakeroot, g++, g++-4.6, libalgorithm-diff-perl, libalgorithm-diff-xs-perl, libalgorithm-merge-perl, libdpkg-perl, libstdc++6-4.6-dev and libtimedate-perl. You'l need to find, download and transfer all of those and all in the correct version and install them:```
sudo dpkg -i some_package.deb
```Correct any errors, rinse and repeat. 


***OR...***

Download and install the 3.8 linux-image I linked and install it:```
sudo dpkg -i linux-image*.deb
```Reboot and done!

Which do you prefer? The links you gave are unlikely to work. I know. The first guy to solve rtl8723ae in Ubuntu was me.

Frankly, if it were my computer, I'd download the DVD for Ubuntu 13.04 and install it and be done in about 15 minutes.

---

### Post by Sam_Wootton on 2013-09-09
Chili555,

I installed Ubuntu 13.04.

And all is working fine - picked up wireless connection no problem.

Thanks for your help. Much appreciated!

Regards, Sam

---

### Post by chili555 on 2013-09-09
Glad it's working! Have fun, Sam.

---

