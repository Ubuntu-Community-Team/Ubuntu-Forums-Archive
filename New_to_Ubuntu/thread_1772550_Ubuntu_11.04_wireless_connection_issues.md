---
title: "Ubuntu 11.04 wireless connection issues"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by gnomemonkey on 2011-05-31
Hi,

I recently got Ubuntu 11.04 dual booted alongside Windows 7. For wireless networks, I can connect perfectly fine on Windows, but for some reason Ubuntu can detect but often doesn't seem able to connect. Usually it's because the signal is weaker (idk why Windows is so much better at connecting then) but sometimes the signal is strong too. Does anyonw know how to fix this? If not, should I maybe overwrite 11.04 with 10.04?

thanks

---

### Post by ubudog on 2011-06-02
Hi there.  Have you installed any wireless drivers?  Can you post the output of lspci:
```
lspci
```

---

### Post by kieubang on 2011-07-17
I have same problem, this ís mine
> ~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LF Gigabit Network Connection (rev 03)
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
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
03:00.0 Network controller: Intel Corporation Ultimate N WiFi Link 5300
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

Please help

---

### Post by HellesAngel on 2011-07-17
Did you search the board?  There are other threads on this too, some with some useful information on them.  The wireless networking does seem a bit unreliable, and the connection is very slow to be established sometimes.  If you are sure you have set it up correctly, ie. correct ESSID and security key, then try being very patient.  Do not interrupt the NetworkManager/NetworkMangler connection, leave it to time out, and try a few times.

While it is running you can open  a terminal and run **sudo iwconfig**.  This should show you the connection state, also **nm-tool** shows the state of the NetworkMangler, **iwscan** will/may show you the WLANs around you.  ** ifconfig** will show you your PCs network adapters.

Debugging a wireless connection from scratch is a several step process - first detecting the hardware installed, loading the correct kernel drivers for it, configuring the wireless connection, then obtaining an IP address and getting DNS working.

---

