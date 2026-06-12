---
title: "Wifi not detected"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by brujoand on 2006-08-20
Hi, my wifi card was not detected by my brand new dapper install.

heres my lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc EHCI USB Controller (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:04.0 Network controller: Agere Systems: Unknown device ab34
0000:02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

any help is apreciated, how can i find my card?

---

### Post by lupine_nickt on 2006-08-20
It'll be this one:-
```

0000:02:04.0 Network controller: Agere Systems: Unknown device ab34

```

A quick google finds the following source code... [http://www.agere.com/mobility/docs/wl_lkm_722_abg.tar.gz](http://www.agere.com/mobility/docs/wl_lkm_722_abg.tar.gz)

...however, a quick chop at compiling it is messy, and an abject failure. I suspect that the driver is incredibly out of date. [here](http://forum.hardware.fr/hardwarefr/OSAlternatifs/installation-carte-WIFI-sous-mandriva-2006-sujet-53236-1.htm) suggests that it's designed for the 2.4 kernel :(, and that there's no native support for Hermes 2/2.5 cards (Which is what it seems to be) in Linux 2.6

So, you've got a few choices. Try to get it working using [ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper). That is the preferred option.

If that doesn't work, then you've got the (extreme, IMO) option of reverting to a 2.4 kernel and trying to compile the driver against that. TBH, that would be a long slog, and the time saved by going and buying a card that works would likely outweigh the material cost.

Your call, though ;)

xF,

...Nick

---

### Post by brujoand on 2006-08-20
thanx, yeah i was wanting to use ndiwrapper, but when i try to extract the inf file using unzip. i get :

unzip ath-ar5001-24244.exe Driver/
Archive:  ath-ar5001-24244.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of ath-ar5001-24244.exe or
        ath-ar5001-24244.exe.zip, and cannot find ath-ar5001-24244.exe.ZIP, period.

any clue on whats wrong?

---

### Post by Aranel on 2006-08-20
> **GrimmVarg said:**
> thanx, yeah i was wanting to use ndiwrapper, but when i try to extract the inf file using unzip. i get :

unzip ath-ar5001-24244.exe Driver/
Archive:  ath-ar5001-24244.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of ath-ar5001-24244.exe or
        ath-ar5001-24244.exe.zip, and cannot find ath-ar5001-24244.exe.ZIP, period.

any clue on whats wrong?

That would be because you're trying to unzip the executable file that would normally install the driver in Windows in a graphical manner. The .sys and .inf files you need are probably elsewhere on the CD. Or, if this is a dual-boot and the driver is already installed in Windows, the files you need can likely be found in C:\WINDOWS\system32\drivers.

I don't know what they're called, but their names probably have something to do with Agere or ab34, which appeared in the lspci output - for instance, the .sys file for my Linksys WPC54G, which is identified as "Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)" by lspci, is bcmwl5.sys.

Good luck!

---

### Post by lupine_nickt on 2006-08-20
Hmm. If that's the provided driver, then it looks like you've actually got an Atheros [AR5001](http://www.windriver.com/cgi-bin/partnerships/directory/viewProd.cgi?id=1403) card. Annoying Agere website giving false info... grr.

You're looking for .inf and .sys files on your driver CD. If you can't find them, then you could try using [these](http://www.wildpackets.com/elements/drivers/Atheros3.0.1.12.zip) or [here](http://www.netgate.com/support/Drivers/STA_24071bin/Install/), for instance.

xF,

...Nick

---

### Post by brujoand on 2006-08-21
Ok, i tried the drivers u suggested. And with:
```
ndiswrapper -i "driver" 
```
i got the driver installed. with ```
ndiswrapper -m 
```
i got it added to modprobe, and ndiswrapper told me that it added the interface wlan0
and then modprobed it befor rebooting..

still it does not show up in ifconfig or iwconfig.. 
btw im running kubuntu on this laptop. I might need som gnome programs?

---

### Post by insyzygy on 2006-08-22
As I recall the ndiswrapper -m command sets it so that wlan0 is associated to the module ndiswrapper. Unless you've changed more configuration files, then wlan0 will not be brought up on boot. 

Try first doing 
```
sudo ifup wlan0 
``` 
and see if the wifi shows up.

---

