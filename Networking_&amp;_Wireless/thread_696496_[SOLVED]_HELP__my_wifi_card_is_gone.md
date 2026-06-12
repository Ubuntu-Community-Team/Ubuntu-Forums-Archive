---
title: "[SOLVED] HELP : my wifi card is gone"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by jake85 on 2008-02-14
hi,

i a noob to linux,

i've been having many problems try to get my Broadcom 43xx wifi card to work.

after installing the driver/firmware in the restricted drivers manager thing looked good.. the wifi appeared to be working but i still could not connect to any AP. i could see the AP but to connect... so i left it alone.

but now i cant even see my wifi card in the network manager or in the restricted drivers manager.

it looks like is gone from my laptop......

can anyone please help, this is really driving me crazy.....

all i did was install a few non-related to wifi apps.... like PHP5, MySQL, Apache ....


i have tried following [http://ubuntuforums.org/showthread.php?t=405990]("http://ubuntuforums.org/showthread.php?t=405990")

but i dont know...... if it will work this time coz last time i did this i had to re-install ubuntu.

any ideas ???? thanks everyone

---

### Post by lswest on 2008-02-14
what card exactly is this?  4311?  because the way i got my card working (Broadcom 4311) was by installing the bcmwl5 driver with ndiswrapper, works like a charm.  If you have the same card, i'll post how i did it.

---

### Post by jake85 on 2008-02-14
i tried 
> i have tried following [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

and i getting this : Unable to detect a Broadcom chipset. Please verify that you have a Broadcom chipset using the 'lspci' command before continuing. If you do decided to install the driver, ndiswrapper installation is highly recommended.

but when i had the broadcom appear in the restricted drivers manage that install showed that i had a broadcom chipset

jakub@jakub-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:07.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:07.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:07.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
jakub@jakub-laptop:~$ 

it looks like my card is gone.........

---

### Post by jake85 on 2008-02-14
i have booted up ubuntu using the live cd

and when i run the lspic command

my wifi card is show up...

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
[COLOR="Red"]**02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)**[/COLOR]
08:07.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:07.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:07.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
08:07.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
ubuntu@ubuntu:~$ 

why is it not showing up when i boot normally ?????

---

### Post by jake85 on 2008-02-14
> **lswest said:**
> what card exactly is this?  4311?  because the way i got my card working (Broadcom 4311) was by installing the bcmwl5 driver with ndiswrapper, works like a charm.  If you have the same card, i'll post how i did it.

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)

thanks for the reply i did some more digging around, as you can see now from my post when i boot live CD it finds it , but when i boot normall it does not???

thanks again, any info is greatly appreciated

---

### Post by jake85 on 2008-02-15
fixed

see : [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")


:lolflag::):):)KS:KS:KS:guitar:

---

