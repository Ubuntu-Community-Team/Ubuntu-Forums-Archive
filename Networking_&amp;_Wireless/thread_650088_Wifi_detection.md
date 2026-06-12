---
title: "Wifi detection"
date: 2007-12-25
forum: Networking &amp; Wireless
---

### Post by jordanae on 2007-12-25
My internal router on my laptop (HP Pavillion dv6000) will not detect any wifi signals. I know there is one because I am using it on my sisters laptop right now. So how do I detect and connect to it?

---

### Post by GSF1200S on 2007-12-26
> **jordanae said:**
> My internal router on my laptop (HP Pavillion dv6000) will not detect any wifi signals. I know there is one because I am using it on my sisters laptop right now. So how do I detect and connect to it?

On your Ubuntu laptop, put the following commands in and paste them here- if you dont have a hard line to post from, perhaps an external HD or a thumb drive will get the terminal printout here?

```
lspci
```

```
iwlist scanning
```

```
iwconfig
```

```
ifconfig
```

```
cat /etc/network/interfaces
```

These codes we need to try and pinpoint why your wireless currently isnt working....

---

### Post by alexmoon on 2007-12-29
Sorry to jump in, but I seem to have the same problem. For me:

**lspci** gives:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV28 [GeForce4 Ti 4200 Go AGP 8x] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI7510 PC card Cardbus Controller (rev 01)
02:01.1 CardBus bridge: Texas Instruments PCI7510,7610 PC card Cardbus Controller (rev 01)
02:01.2 FireWire (IEEE 1394): Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller
02:01.3 System peripheral: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function
02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

**iwlist scanning** gives:
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

**iwconfig** gives:
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"DLINK"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and **/etc/network/interfaces** reads:
auto lo
iface lo inet loopback

---

### Post by alexmoon on 2008-01-01
Sorry, just wondering if there was any further news on this, since I'm still stuck. Jordanae - did you manage to sort it out?

---

### Post by kevdog on 2008-01-01
Ok you have a broadcom wireless card.  Did you install a driver??

lshw -C network

---

### Post by alexmoon on 2008-01-02
I did have a driver installed - a bit of additional fiddling (rather embarrassingly, including turning on wireless in the BIOS) means I can now see several networks. I can't work out how to connect to them yet, but I guess that's a problem for another thread. Thanks for the help kevdog and I hope jordanae works it out.

---

