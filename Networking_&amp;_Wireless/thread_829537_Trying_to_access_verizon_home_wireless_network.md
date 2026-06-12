---
title: "Trying to access verizon home wireless network"
date: 2008-06-14
forum: Networking &amp; Wireless
---

### Post by todd2000 on 2008-06-14
I'm using Gnome in 8.04 on a HP laptop and I'm trying to access a verizon home wireless network but it does not seems to pick up the network. I'm not even sure if my wireless card is working in Ubuntu or if I need to set it up. I did the following to make sure I don't have one of the Broadcom cards so many people have problems with.

```
laptop:~$ lspci | more
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Is my card functioning? How can I check it since it is not showing up in the NetworkManager Applet.

Thanks, Todd

---

### Post by Jaxl on 2008-06-24
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

well it appears to me that its being read as a memorey stick for a digital camera i have no clue check you configurations again somethins messed

---

### Post by pokipoki08 on 2008-06-24
This is your wireless card

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Please post the output of these commands
```
dmesg | grep wlan
```
```
cat /var/log/messages | grep wlan
```

---

### Post by timcredible on 2008-06-24
what wireless router did verizon give you?  if it's a westell, you might need to upgrade the router - i had to in order to get my dell vostro to connect.  it's not too difficult to upgrade the router, but you have to use windows to do it.

---

### Post by Jaxl on 2008-06-24
> **pokipoki08 said:**
> This is your wireless card

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Please post the output of these commands
```
dmesg | grep wlan
```
```
cat /var/log/messages | grep wlan
```

xD didnt see that just skimed the page xD

---

