---
title: "toshiba nb 200"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by pjfleming on 2010-01-19
very new to ubuntu - am trying to get bluetooth to work - applet says no adaptor but have built in bluetooth - can someone please point me in right direction including how to use "code" etc
thanks in advance

ps really like interface

---

### Post by audiomick on 2010-01-19
Hi.
I don't think I will be able to help, but do
```
lspci
```in the terminal and post the output here. That should show that the bluetooth adapter is being found at boot or not, as far as I know.

---

### Post by pjfleming on 2010-01-19
as far as i can tell adapter is not being detected - works fine in xp but don't want to go back   - help please

---

### Post by nick_goodfate on 2010-01-20
Hi! i have the same problem . i dont understand how the output of lspci could help , but here is mine :
> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
0a:01.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
0a:01.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0a:01.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by lisati on 2010-01-20
> **nick_goodfate said:**
> Hi! i have the same problem . **i dont understand how the output of lspci could help** , but here is mine :
If it's a USB device then the output from lsusb might be better. Both lspci & lsusb can be used to show what devices are being recognized by Ubuntu.

*Note: Not all models in a particular range are created equal. I have an M200 which doesn't have bluetooth built in but other versions of the M200 apparently do.*

---

### Post by nick_goodfate on 2010-01-20
ok. in my uotput i cant see any bluetooth adapter , right ? can i do something so it can see the adapter which i m sure it exists !

---

### Post by audiomick on 2010-01-20
Hi Nick.
No, there is apparently no bluetooth in you output.
Have you also tried
```
lsusb
```

Some times those things are connected via usb, even when they are built in, I believe.
That's the first step, anyway: see if the computer is seeing the thing. Then you know where to start looking for the problem.

---

### Post by nick_goodfate on 2010-01-20
nothing with lsusb , i also tried lshw and its not there ... is there any easy solution ? its not so importand for me but as its there why not to work ... best english you ve ever read ?:p

---

