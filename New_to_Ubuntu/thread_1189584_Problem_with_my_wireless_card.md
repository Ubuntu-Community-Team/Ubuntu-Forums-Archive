---
title: "Problem with my wireless card"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by judavi on 2009-06-16
Hi!

I'm newbie, and don't talk to much english, but I will try expose my problem.

I'm triying to pass my wireless card to master mode doing this

iwconfig wlan0 mode master

and receive this mesagge

SET failed on device wlan0 ; Operation not permitted.

after I tried to do this

sudo rmmod ath_pci; sudo modprobe ath_pci autocreate=ap

and received this message

module ath_pci does not exist in /proc/ atheros pci

Please I need to convert my Wireles card to master mode to make an acces point.

Thanks,

---

### Post by PmDematagoda on 2009-06-16
Did you try using the iwconfig command with sudo?

---

### Post by judavi on 2009-06-16
Yes, I tried

sudo iwconfig wlan0 mode master

and have the same problem,

Thanks for reply fast :)

---

### Post by RiceMonster on 2009-06-16
Two things, if you're using the ath_pci driver, it usually creates an ath0 wireless interface, rather than wlan0 (that's my experience at least).

Also, you may need the ath5k module, rather than ath_pci. If you're using ath5k, it should create a wlan0 interface (again, my experience).

If you're confused, post the output of iwconfig and lspci.

---

### Post by judavi on 2009-06-16
> **RiceMonster said:**
> Two things, if you're using the ath_pci driver, it usually creates an ath0 wireless interface, rather than wlan0 (that's my experience at least).

Also, you may need the ath5k module, rather than ath_pci. If you're using ath5k, it should create a wlan0 interface (again, my experience).

If you're confused, post the output of iwconfig and lspci.

When I type iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


.... so now...?

---

### Post by judavi on 2009-06-16
> **RiceMonster said:**
> Two things, if you're using the ath_pci driver, it usually creates an ath0 wireless interface, rather than wlan0 (that's my experience at least).

Also, you may need the ath5k module, rather than ath_pci. If you're using ath5k, it should create a wlan0 interface (again, my experience).

If you're confused, post the output of iwconfig and lspci.


lspci....

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
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
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
08:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by RiceMonster on 2009-06-16
Ah, so ath_pci is the right driver and wlan0 is the right interface. So, what I thought was the problem, was not the case. Sorry, but I can't solve your problem.

---

### Post by iponeverything on 2009-06-16
remove the ath_pci module and re-add it:

```
modprobe ath_pci autocreate=ap

```

make the change permanent with:
```
options ath_pci autocreate=ap
```

modprobe ath_pci autocreate=ap

The documentation that came with madwifi driver source is pretty good.

---

### Post by judavi on 2009-06-16
> **iponeverything said:**
> remove the ath_pci module and re-add it:

```
modprobe ath_pci autocreate=ap

```make the change permanent with:
```
options ath_pci autocreate=ap
```modprobe ath_pci autocreate=ap

The documentation that came with madwifi driver source is pretty good.


mmm... please wait... I'm new with this...

the first step is ....

modprobe ath_pci autocreate=ap

and the second is...

options ath_pci autocreate=ap

no more?? 

:)

---

### Post by judavi on 2009-06-16
lestat@Navy:~$ options ath_pci autocreate=ap
bash: options: orden no encontrada

..... I have problems with the second comand

---

### Post by iponeverything on 2009-06-16
Sorry about that.

To make change permanent add this line /etc/modprobe.d/options

 ```
options ath_pci autocreate=ap
```

An easy way to do this is with this command:

```
sudo echo options ath_pci autocreate=ap >> /etc/modprobe.d/options
```

---

### Post by judavi on 2009-06-16
lestat@Navy:~$ sudo echo options ath_pci autocreate=ap
options ath_pci autocreate=ap
....

or its with

sudo echo options ath_pci autocreate=ap >> /etc/modprobe.d/options

have this reply
bash: /etc/modprobe.d/options: Permiso denegado

---

