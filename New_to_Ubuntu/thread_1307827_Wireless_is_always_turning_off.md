---
title: "Wireless is always turning off"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Nottawa on 2009-10-31
After reading some of the other users wireless problems, mine is trivial, but it annoys me:  Whenever I come back to my computer after it has been turned off, hibernated or suspended, my wireless has been disconnected.   Is there a way to keep that from happening?  I'm running 9.04 on a Thinkpad T400 with 3 gigs ram and an Intel Wifi card.  It works great, it is just having to turn it on every time I come back to the computer.

---

### Post by admiralspark on 2009-10-31
Would you mind posting up the output of:
> lspci
So that we can see the specific model of the card. Also, I'm going to assume you're using the factory drivers to handle the wireless?

And just so I make sure that I'm clear on the problem, you mean that the wireless itself shuts off, not just disconnects?

---

### Post by Nottawa on 2009-10-31
Admiralspark:  I guess the correct thing is that it disconnects.  I am used to Vista where it automatically reconnects when I start up the computer again.  

The command you want me to run: The first character: is that an l(L) or a 1 (one)?  I just enter that in terminal?  Or in some other program?

As for the driver, I am using the factory supplied ones, unless Ubuntu changed them on setup.

---

### Post by anewguy on 2009-10-31
The command starts with a lower case "L" and what it does is list (ls) the pci device (hence lspci) on your system.  I'll leave the rest to them.

Dave :)

---

### Post by Nottawa on 2009-10-31
Thank you Dave.  Here is the result:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
peter@peter-laptop:~$ 

I see that the WiFi is a 5300 model.

---

