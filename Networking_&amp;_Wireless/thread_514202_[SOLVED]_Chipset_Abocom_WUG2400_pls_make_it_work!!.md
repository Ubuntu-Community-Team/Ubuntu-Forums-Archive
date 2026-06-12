---
title: "[SOLVED] Chipset Abocom WUG2400 pls make it work!!!"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by Funkey Monkey on 2007-07-31
Hi,
I have a usb wireless adapter, but its not working out of the box.
System -> Admin -> Network  only has my wiredlan and modem

I have used search function but there is no definitive guide for my device.

Its a Mecer Mini Wireless Lan Usb 2.0 Adapter.
I phoned them and they said the chipset is a Abocom WUG2400.

I googled it and a website said the Chipset is TNET1450
and it also says someting about ACX111
[COLOR="YellowGreen"]http://acx100.sourceforge.net/matrix.html[/COLOR]

I`m Running the Desktop version of Ubuntu 7.04 Feisty Fawn
My lsusb gives:
xxx@desk:~$ lsusb
Bus 004 Device 004: ID 07b8:b21a D-Link Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c044 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000 

And lspci gives:
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2)


I think that Ndiswrapper is the only option for me but the guide is a bit confusing for a person just stepping into the light.
[COLOR="YellowGreen"]https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper[/COLOR]
Another website I found regarding ACX111
[COLOR="YellowGreen"]https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111[/COLOR]

Can someone please help me to install the wifi device without breaking feisty???

---

### Post by Funkey Monkey on 2007-08-06
See my other post for results
[http://ubuntuforums.org/showthread.php?t=516347&highlight=abocom](http://ubuntuforums.org/showthread.php?t=516347&highlight=abocom)

---

