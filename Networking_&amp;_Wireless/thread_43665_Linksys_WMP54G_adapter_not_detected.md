---
title: "Linksys WMP54G adapter not detected"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by TimTheEnchanter on 2005-06-22
Hi all,

I've got an onboard ethernet connection (which I'm using now) but I'd like to use my Linksys wireless card so I can move this box somewhere else in the apartment. 

I tried to follow the ndiswrapper guide at [https://wiki.ubuntu.com//HowToSetUpNdiswrapper](https://wiki.ubuntu.com//HowToSetUpNdiswrapper) but got a fatal error that stated the 'operation could not be performed.' After some research I figured it'd be prudent to check if there was even a 2nd card detected:

```

# lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02 )
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4a49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4a69
0000:02:01.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)
0000:02:03.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)

```

Does anyone see another NIC in there? I'm at a loss right now, as I don't know how to show Ubuntu that there's another card hanging out. 

This box is a dual-booting machine with XP on the other side that uses the wireless adapter without a problem.

Thanks!

---

### Post by rachii on 2005-06-22
did ndiswrapper install the driver?
try ```
ndiswrapper -l
```  does it show that card is installed properly?

---

### Post by JettCRX on 2005-06-23
```

# lspci
0000:00:00.0 Host bridge: Intel Corp. 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82865G/PE/P PCI to AGP Controller (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev c2)
0000:00:1f.0 ISA bridge: Intel Corp. 82801EB/ER (ICH5/ICH5R) LPC Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801EB/ER (ICH5/ICH5R) Ultra ATA 100 Storage Controller (rev 02 )
0000:00:1f.3 SMBus: Intel Corp. 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4a49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4a69
**0000:02:01.0 Network controller: RaLink Ralink RT2500 802.11 Cardbus Reference Card (rev 01)**
0000:02:03.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:08.0 Ethernet controller: Intel Corp. 82562EZ 10/100 Ethernet Controller (rev 02)

```

I have the same card.  Make sure you are using Ralink drivers and not Broadcom ones.  The Broadcom drivers won't work with this card.

The steps I followed are here:  [http://www.ubuntuforums.org/showthread.php?t=42193&highlight=Linksys+WMP54G](http://www.ubuntuforums.org/showthread.php?t=42193&highlight=Linksys+WMP54G)

---

