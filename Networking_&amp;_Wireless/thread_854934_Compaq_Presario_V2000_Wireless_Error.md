---
title: "Compaq Presario V2000 Wireless Error"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by tawnos on 2008-07-10
As the title states, I'm having an issue with the wireless on my Compaq Presario V2000. After hours of troubleshooting I finally managed to install the drivers for the card and now it locates wireless networks.. only problem is when i try to connect it hangs when i goes to obtain IP. I tried the normal wireless manager, WiFi-Radar, and WICD. All i get the same issue, it wont connect. I have tried multiple unsecured and networks so i know i'm not inputing the wrong password. I'm running on the latest version of Ubuntu 8.04.

Any help would be greatly appreciated.

---

### Post by superprash2003 on 2008-07-10
go to system->admin->network and try setting up a connection manually.. i.e. by setting up a static ip etc..

---

### Post by tawnos on 2008-07-10
Thank you for the suggestion, but thats not a good option for me. What if I'm trying to connect to a Wi-Fi spot at a random place and i don't know the DNS, Ip, Gateway, etc...

Also, it managed to connect to the wireless here at work (it too is unsecured) however it wont connect to the wireless at the house which is unsecured or my phone (I can turn my phone in a Wi-Fi spot N95 with JoikuSpot)

Any ideas?

---

### Post by tawnos on 2008-07-10
dont know if this will help?


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller

---

### Post by superprash2003 on 2008-07-10
ensure that DHCP is enabled in your wifi router

---

### Post by tawnos on 2008-07-10
What if i dont have access to the router? + i can connect to it from other devices such as my phone, and my other laptop....

Any ideas?

Thanks for the help guys.

---

### Post by tawnos on 2008-07-10
Also, when i try to connect to the wifi my phone gives off its an ad-hoc but i cant seem to get an IP from it either.. also its unsecured. ive been able to connect to it form other computers.

Any suggestions?

Thanks :)

---

### Post by superprash2003 on 2008-07-10
you would have to check the router settings.. could be the dhcp range is very less or the other computers are connecting via static  ip!!

---

### Post by tawnos on 2008-07-11
I tried connecting with static IP and it said it connected and it even gave me a connecting Mbps rate but when i tried to use internet it would not work it would just time out...

---

### Post by tawnos on 2008-07-11
Can you guys suggest for me a card either USB or PCMCIA that will just work with Ubuntu Hardy?

Thank you for all the help.

---

### Post by tawnos on 2008-07-11
Bump?

Thanks a lot for any help guys :)

---

### Post by tawnos on 2008-07-13
any one?

Thanks

---

### Post by jdramer on 2008-08-05
When I was trying to set up Hardy on my V2000 the wireless adapter would show up in the IP list, but couldn't get an IP.  In the end it still turned out that it was a driver issue.
To get the right driver I just ran
```
sudo apt-get install b43-fwcutter
```
It downloaded the firmware and installed it.  It also mentioned that ndiswrapper needed to be disabled, but I didn't have it enabled.  After a reboot the LED for the wifi turned on and I could connect to my router (WPA encrypted).

---

### Post by Doy22 on 2008-08-11
I have a Compaq Presario v2000 laptop that I got from a friend to fix. When it boots up, it will beep... shut off... turn on again... beep... and it does this until you hold the power button and turn it off for good. I don't see anything at all on the screen. I hear the hard drive spinning and the CPU fan running, but that is it. I don't hear any audio from the computer except for the beeps.

What could this be and how do I fix it? Is it something wrong with the bios? My friend said that he might have gotten a virus. Is this possible to affect the computer in this way. How likely would that be?

---

### Post by JokeDog on 2008-08-22
no...can't be a virus.  That's a hardware issue.  During boot, everything is read from ROM. If nothing displays during this stage, your integrated video card is shot.  You should see all those ROM/BIOS info.  This is way before the software/virus stage. The beep pattern will tell you what the problem is.  Look up compaq/HP support site.

As for the author of this tread....sorry no one can help you, but it would be nice if you can share how you get Ubuntu to recognize your internal wireless card to save people like me the hours you wasted.  Forum is not about getting info, but giving as well.  You'll find more people willing to help you when you start to share those info.

---

### Post by JokeDog on 2008-08-22
I was able to get ubuntu wireless working on my compaq presario v2000 a while ago, but my wireless indicator doesn't even light on.  Anyway, if you can't get it to work, you can tried [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)  that was how it got my to work previously.

---

