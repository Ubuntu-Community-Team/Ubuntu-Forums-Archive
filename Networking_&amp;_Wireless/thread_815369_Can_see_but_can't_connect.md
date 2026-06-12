---
title: "Can see but can't connect"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by i40hawk on 2008-06-01
I have an Asus wl-138g v2. I am using the Restricted Drivers that Hardy automatically detected. I can see my network but i can't connect. The network is configured with WPA2 Personal Security with the AES algorithm. I tried connecting using both roaming mode and configured specifically to my network. I am a relative newbie, so no really complex command line please.

---

### Post by Absurdiverse on 2008-06-01
Can you run lspci in the terminal please.

---

### Post by i40hawk on 2008-06-01
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 02)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
00:09.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 09)
00:0a.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 02)
00:0a.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 02)
[COLOR="Red"]00:0c.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/COLOR]
00:0d.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
There is the output with the wifi card highlighted

---

### Post by Corrupt3d on 2008-06-01
Hello i40hawk,

I'm having the same problem as you, I have a Laptop with the same Broadcom chipset :: **BCM4318 (rev 02)**. 
I was able to get online using the ndiswrapper,  however the card keeps dropping me after a few hours. :( 
I can see all the Networks but connecting to them seems impossible!

Take a look at the documentation for this chipset:
[quote=]Works on and off with both Ndiswrapper and Fwcutter methods. 
The majority of the difficulty is just getting the connection. Ndiswrapper method has been working the best.
[[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadco]([URL="https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom"]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadco)m]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom")[/quote]

The only way I seem to be able to re-establish a connection is by reseting my Router and then trying again.

---

