---
title: "Wifi doesn't work"
date: 2018-05-10
forum: Networking &amp; Wireless
---

### Post by jap364 on 2018-05-10
Hello, I'm clompletely new to Xubuntu. I had an old Dell laptop which ran really slow, so I thought I'd try Xubuntu. The installation went smothly, but an error appeard. Unfortunately I don't remember what it said. The OS workes  great, but I cannot connect to the internet. Two grey arrows appear on the wifi symbol, and when I open the "configure networks" it's empty.
My laptop is a Dell Inspiron 1420

PS: sorry for my bad english

---

### Post by oldrocker99 on 2018-05-11
It is possible (though unlikely) that the driver for your network card is not in the kernel.

Please post the results of ```
lspci
```

That'll show the model of the wireless chip, and we can work from there.

---

### Post by leunam12 on 2018-05-11
Sometimes there is an on/off button (or keyboard key) for the WIFI card, if your computer has one, make sure that
the card is ON.

---

### Post by slickymaster on 2018-05-11
Thread moved to **Networking & Wireless** for a better fit

---

### Post by jap364 on 2018-05-11
> **oldrocker99 said:**
> It is possible (though unlikely) that the driver for your network card is not in the kernel.

Please post the results of ```
lspci
```

That'll show the model of the wireless chip, and we can work from there.
 Hi, the results are:
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Limited NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Limited BCM4311 802.11b/g WLAN (rev 01)

```

---

### Post by jap364 on 2018-05-11
> Sometimes there is an on/off button (or keyboard key) for the WIFI card, if your computer has one, make sure that
the card is ON
My laptop does not have a Wifi button.

On a final note, I put an antenna on the USB port and now it seems to work.

---

### Post by praseodym on 2018-05-11
Install this firmware package

```
wget https://media-cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz  
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot

---

### Post by Autodave on 2018-05-11
If all else fails.....

This may or may not help, but it is the very first thing that I do when I get a weird thing happening on a laptop:

1. Power down and disconnect power cord.
2. Unplug all peripherals.
3. Remove battery.
4. Wait 10 minutes.
5. Reinstall battery.
6. Connect power cord.
7. Boot computer and test to see if condition is gone.
8. If good so far, now you can reconnect peripherals.

---

### Post by jap364 on 2018-05-12
I ended up putting peripheral on the usb port and now it works. Thank you yo much for answering.

---

