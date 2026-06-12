---
title: "No Wifi card recognised, after recompiling kernel."
date: 2006-11-24
forum: Networking &amp; Wireless
---

### Post by ebichu on 2006-11-24
Hey, guys.
Yesterday I recompiled my kernel, everything worked out fine, except, that I don't have my wifi card recognised.
I'm running Intel's motherboard. Don't know exact model. Sorry.
So the basic question. Would recompiling the kernel help? Or maybe i should modprobe something?
Sorry for maybe stupid questions and definetly bad english (not my primary language). If you need anything more, then ask away.

---

### Post by zgornel on 2006-11-24
Post a *lspci* please.

---

### Post by ebichu on 2006-11-24
```
ebichu@delirium:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
01:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
01:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
01:04.2 Class 0805: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
01:04.4 FLASH memory: ENE Technology Inc Unknown device 0551 (rev 01)
```

---

### Post by zgornel on 2006-11-24
Ok, the wireless card is : 01:02.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05). Check in /lib/modules/<kernel version>/drivers/net/wireless for the ipw3945 directory and inside it the module (.ko). If there is one, run *lsmod* to see if the ipw3945 is listed among the loaded modules. If it is not listed but the module exists, run *insmod ipw3945* and see if it loads it. If there isn't any module, recompile the kernel. Also, run *dmesg* and search for the lines refering to wireless (if there are any). You might get some info from there too.

PS. If you have not did this, do it: Create a directory in /lib/firmware with the name of your kernel (you get the name by running *uname -r*). There should be another directory there (of the old kernel) - copy its contents into the newly created directory so the newly compiled drivers can read the firmware

---

### Post by ebichu on 2006-11-24
dmesg contained
[   16.447000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
and 
[   16.452000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
and lsmod tells me that ipw2200 module is loaded, but somehow, no Network setting show me that i have a wifi card. : (

---

### Post by zgornel on 2006-11-25
Ooops, I was wrong, I thought you had a i3945 wireless chipset. Anyway, the drivers for the wireless card are loaded, if you have the firmware in the right place, it should be ok. Check for the firmware or copy it in the right location as I mentioned in the previous post.

---

### Post by ebichu on 2006-11-25
Thanks, zgornel, it works again. ^^

---

### Post by zgornel on 2006-11-25
Glad to hear it.

---

### Post by strabes on 2007-06-30
I'm having the same trouble. I just recompiled from 2.6.20-16-generic to 2.6.21 with a patch to get my microsoft natural ergonomic keyboard working. Here's the output of some of the commands you said above:

> alex@alex-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

> alex@alex-laptop:~$ ls /lib/modules/2.6.21/kernel/drivers/net/wireless/
airo_cs.ko  atmel_cs.ko   bcm43xx    ipw2100.ko     orinoco_cs.ko      orinoco_pci.ko  ray_cs.ko       wavelan_cs.ko  zd1201.ko
airo.ko     atmel.ko      hermes.ko  ipw2200.ko     orinoco.ko         orinoco_plx.ko  spectrum_cs.ko  wavelan.ko     zd1211rw
arlan.ko    atmel_pci.ko  hostap     netwave_cs.ko  orinoco_nortel.ko  orinoco_tmd.ko  strip.ko        wl3501_cs.ko

> alex@alex-laptop:~$ dmesg | grep wireless -i
[   89.324000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq

- the problem with this one is that it's not the right driver for my card (3945abg)

> alex@alex-laptop:~$ uname -r
2.6.21

I ran the following commands, rebooted, and it still doesn't appear in iwconfig or anything:

```
sudo mkdir /lib/firmware/2.6.21
sudo cp -r /lib/firmware/2.6.20-16-generic/* /lib/firmware/2.6.21
```

---

