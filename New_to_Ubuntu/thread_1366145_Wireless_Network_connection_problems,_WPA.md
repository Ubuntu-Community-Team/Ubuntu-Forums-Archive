---
title: "Wireless Network connection problems, WPA"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by newwb on 2009-12-28
This has got me puzzled...whenever I try to connect to my wireless network (WPA Personal), I always get the message "Authentication Required", but in the drop down menu for wireless security it does not show WPA, only WEP options, therefore I am unable to connect. I am able to see wireless networks, including my own, so I know the wireless card is working. I've tried changing the option countless times in the wireless network connections settings; a WPA option IS in that particular drop down menu, but once I try to connect again I get the same authentication message and it does not give me a WPA option to choose from, only WEP.    :confused:

I am running a newly installed Ubuntu 9.10 on a older Dell laptop 

any help would be greatly appreciated.

---

### Post by Blackthorne2 on 2009-12-28
I am having the same issue. I see wireless networks no problem, but I do not have the option for WPA.

The wpasupplicant package shows as installed on my TC1000. And I can connect to non encrypted wifi connection without any trouble.


Verison 9.10 on Compaq TC1000

---

### Post by newwb on 2009-12-28
bump

---

### Post by newwb on 2009-12-28
bump

---

### Post by newwb on 2009-12-28
....anyone want to help us out? I've installed ndiswrapper and wpa_supplicant is up to date, I've even edited the network interfaces with no avail. I am just getting a bunch of error messages like "wpa_supplicant daemon failed to start" among others. I've looked up a bunch of tutorials and nothing seems to work.

would REALLY like some help here.

---

### Post by fibercode on 2009-12-28
First off... what is your wireless chipset?

Can you post the out put of this command:

```
lspci
```

---

### Post by Blackthorne2 on 2009-12-29
> **fibercode said:**
> First off... what is your wireless chipset?

Can you post the out put of this command:

```
lspci
```

Here you go. Funny..I jsut thought of the fact that this WIFI card might simply be too old to run WPA LOL.


00:00.0 Host bridge: Transmeta Corporation LongRun Northbridge (rev 03)
00:00.1 RAM memory: Transmeta Corporation SDRAM controller
00:00.2 RAM memory: Transmeta Corporation BIOS scratchpad
00:05.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:07.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 30)
00:08.0 Ethernet controller: Intel Corporation 82551QM Ethernet Controller (rev 10)
00:0a.0 Ethernet controller: Atmel Corporation at76c506 802.11b Wireless Network Adaptor (rev 11)
00:0b.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
00:0b.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
00:0c.0 USB Controller: NEC Corporation USB (rev 41)
00:0c.1 USB Controller: NEC Corporation USB (rev 41)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 02

---

### Post by newwwb on 2009-12-29
I have also thought my wireless card is out of date, except the fact that winxp was able to connect to WPA just fine. 

	> 00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)  
 00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)  
 00:03.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller  
 00:03.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller  
 00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)  
 00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)  
 00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)  
 00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)  
 00:08.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)  
 00:10.0 Ethernet controller: 3Com Corporation 3c556 Hurricane CardBus [Cyclone] (rev 10)  
 00:10.1 Communication controller: 3Com Corporation Mini PCI 56k Winmodem (rev 10)  
 01:00.0 VGA compatible controller: ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02)  


any help is greatly appreciated. Even if I am forced to upgrade my wireless card I will be happy to know that is the central problem.

---

### Post by bkratz on 2009-12-29
> **newwwb said:**
> I have also thought my wireless card is out of date, except the fact that winxp was able to connect to WPA just fine. 

	

any help is greatly appreciated. Even if I am forced to upgrade my wireless card I will be happy to know that is the central problem.

@newwwb

Since your wireless card doesn't show up in your lspci listing, is it a usb device?  If so, post lsusb

---

### Post by newwb on 2009-12-29
> **bkratz said:**
> @newwwb

Since your wireless card doesn't show up in your lspci listing, is it a usb device?  If so, post lsusb


it's actually a Linksys Instant Wireless Network PC Card (model WPC11). Could this have been my problem all along?

---

### Post by FinalCoyote on 2009-12-29
Dunno, shouldn't matter should it?

Mine didn't like WPA-Personal to begin with either, but strangely enough after a reboot it started working no problem.

---

### Post by bkratz on 2009-12-29
> **newwb said:**
> it's actually a Linksys Instant Wireless Network PC Card (model WPC11). Could this have been my problem all along?

Well the WPC11 is a pci type card and it should have shown up. I believe  lspci | grep Wireless   should just show the wireless card and not all the extra stuff.  Is there some type of switch or bios setting that could have turned it off? The switch could be a series of keystrokes.  Also if it was not shut off correctly last time you were in windows, I believe you can put it in a non-working condition ( not really sure of this though).


Well I went back and read the original posting and see that it is about something other than the card not working.  I still can't explain why the card does not show up, but it must have drivers and basic functionality if you can see local networks.  Here is a link to  someone who is trying to update the flash on his/her card to use WPA encryption, apparently the card is old enough to possibly not support it natively.  Anyway,

[http://ubuntuforums.org/showthread.php?t=1171138&highlight=WPC11](http://ubuntuforums.org/showthread.php?t=1171138&highlight=WPC11)

Might be useful.

---

