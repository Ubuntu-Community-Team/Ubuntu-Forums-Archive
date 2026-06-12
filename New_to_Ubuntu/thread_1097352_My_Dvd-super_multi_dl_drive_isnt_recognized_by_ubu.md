---
title: "My Dvd-super multi dl drive isnt recognized by ubuntu"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by afatyan on 2009-03-15
Hello every one, I am pretty sure you guys get these all the time but I am really desperate, I need my dvd/cd drive to work.  Please help me asap. thanks.

---

### Post by supersonicdarky on 2009-03-15
Hard to help without any info.

- Ubuntu version
- Exact drive model

---

### Post by afatyan on 2009-03-15
sorry,

Ubuntu version is 8.10 , the drive info, I dont really know because it came with the laptop and I didnt know how to find out what it is .any idea how i can find out?

---

### Post by Mark Phelps on 2009-03-16
From a terminal, enter "lspci".

---

### Post by halitech on 2009-03-16
lspci won't do much good as it doesn't list drives. from the terminal post the output of
```
lshw -C disk
```

---

### Post by afatyan on 2009-03-16
Thanks guys for the reply and concern!

Here are both the results:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
04:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
0f:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0f:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
0f:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
0f:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

```

And

```
  *-disk                  
       description: ATA Disk
       product: WDC WD1600BEVS-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 04.0
       serial: WD-WXC807513461
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=561138b6

```

Any idea what I can do?

---

### Post by halitech on 2009-03-16
that is the same info in both. what was the output of ```
lshw -C disk
```

---

### Post by afatyan on 2009-03-16
Yea this is it,


  *-disk                  
       description: ATA Disk
       product: WDC WD1600BEVS-2
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 04.0
       serial: WD-WXC807513461
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=561138b6

---

### Post by halitech on 2009-03-17
another one not showing cd/dvds. whats the make of the laptop, maybe we can find out what the drive is.

---

### Post by afatyan on 2009-03-17
Ok, it is an Acer Extensa 4620-4605

Thanks for your efforts

---

### Post by afatyan on 2009-03-18
Anyone?

---

### Post by halitech on 2009-03-21
unfortunately the acer website doesn't help much with models of drives, just what possible combinations they might use. I'm not sure but this is the second system I've run across that after the install has no optical drives showing up. Might be a bug but not sure. Just going to bump because I'm out of ideas.

---

