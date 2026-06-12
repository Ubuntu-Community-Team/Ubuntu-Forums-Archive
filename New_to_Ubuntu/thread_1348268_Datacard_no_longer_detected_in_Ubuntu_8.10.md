---
title: "Datacard no longer detected in Ubuntu 8.10"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by anjali.thampi on 2009-12-07
Hi, 

  I use Ubuntu 8.10 (amd_64) on a Dell Latitude D630 laptop.I have been using Huawei EC321 Tata Indicom datacard which suddenly stopped working.As far as I remember, I did not run any upgrades.My datacard works fine on a windows laptop.I have tried restarting the system with and without the datacard.The datacard is not detected using lsusb, pccardctl,lspci.I am at my wit's end.HELP!!
 
Is there any command to check if my pcmcia slot is working fine?

  uname -a
 ```

Linux ubuntu 2.6.27-14-generic #1 SMP Mon Aug 31 12:58:38 UTC 2009 x86_64 GNU/Linux
```lsusb
```

Bus 006 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 006 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```lspci 
```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
```pccardctl status
```
Socket 0:
  no card

```pccardctl ls
```
Socket 0 Bridge:       [yenta_cardbus]     (bus ID: 0000:03:01.0)

```pccardctl ident
```
Socket 0:
  no product info available

```pccardctl info
```
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

```

pcs_scan : (This is inspite of having the datacard in the slot)
```
PC/SC device scanner
V 1.4.14 (c) 2001-2008, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.99
Scanning present readers
0: O2 Micro Oz776 00 00

Mon Dec  7 15:26:29 2009
 Reader 0: O2 Micro Oz776 00 00
  Card state: Card removed, 
```

Also please find output of lspci -v and dmesg as attachment.

---

