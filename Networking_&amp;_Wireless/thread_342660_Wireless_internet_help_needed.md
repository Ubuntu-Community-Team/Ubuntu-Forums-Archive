---
title: "Wireless internet help needed"
date: 2007-01-20
forum: Networking &amp; Wireless
---

### Post by Leela on 2007-01-20
Hey,
I installed Ubuntu on my computer today, and everything is working fine... 
Except... Connection to my wireless internet... I tried searching for help, I found alot, but as i've never worked with linux, I don't understand half what they are saying...
I got a SMC router and are only 2-3 metres from my router.

Thanks in advance
Leela

---

### Post by teaker1s on 2007-01-20
terminal type these commands and post results

[COLOR="Red"]lspci

lsusb

iwconfig[/COLOR]

---

### Post by Leela on 2007-01-20
LSPCI
```

00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
04:00.1 Display controller: ATI Technologies Inc RV370 secondary [ATI Sapphire X550 Silent]
```

LSUSB
```
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:7004 Hewlett-Packard DeskJet 3320c
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c30e Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

IWCONFIG
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

---

### Post by teaker1s on 2007-01-20
> **Leela said:**
> LSPCI
```

00:00.0 Host bridge: Intel Corporation 945G/GZ/P/PL Express Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 945G/GZ/P/PL Express PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
[COLOR="RoyalBlue"]01:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)[/COLOR]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
04:00.0 VGA compatible controller: ATI Technologies Inc RV370 [ATI Sapphire X550 Silent]
04:00.1 Display controller: ATI Technologies Inc RV370 secondary [ATI Sapphire X550 Silent]
```

LSUSB
```
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 03f0:7004 Hewlett-Packard DeskJet 3320c
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c30e Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
```

IWCONFIG
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.
```

looks as if the wireless has no driver/firmware as we would expect that something would show in iwconfig. I have highlighted your wireless in blue. I'll look round for you and post any helpful links I find

looks to work with ndiswrapper and windows drivers or look at this thread
[http://ubuntuforums.org/showthread.php?t=208088&highlight=88w8335]("http://ubuntuforums.org/showthread.php?t=208088&highlight=88w8335")

---

### Post by Leela on 2007-01-20
I looked at the website of SCM, and it looks like there's no driver (needed) for my router... Is that a problem or not?
Cuz on the link you've send it says 'After I finished this step, I downloaded the wireless driver from ...'

---

### Post by teaker1s on 2007-01-20
most routers don't need software to configure them they can be configured by accessing them via a web browser. most common addresses are
192.168.0.1
192.168.1.1

some routers have default ip and user and password on underneath stamped or printed on a sticker-otherwise check your documentation

generally the windows router software allows  links to router settings,docs and not much more

---

