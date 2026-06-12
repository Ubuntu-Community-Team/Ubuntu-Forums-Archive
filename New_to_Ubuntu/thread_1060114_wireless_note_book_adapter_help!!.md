---
title: "wireless note book adapter help!!"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by greypatch on 2009-02-04
Hey guys I have a linksys WPC54GX ver.2 network adapter and I dont know if its compatible with ubuntu. Im installing ubuntu on my old laptop right now and would like to know if its compatible. If not what are some good compatible notebook adapters?

---

### Post by petervk on 2009-02-04
If you have ubuntu up and running, just not the wireless. Launch a terminal and run the lspci command, and somehow post the results of that here. (Put it in a text file and save it to a usb key?)

We can use that to help determine if your card will work with ubuntu.

---

### Post by greypatch on 2009-02-04
ok so I found the terminal and ran the command. Heres what I got

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:05.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev b8)
02:05.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C551 IEEE 1394 Controller
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
03:00.0 Ethernet controller: Airgo Networks Inc AGN100 802.11 a/b/g True MIMO Wireless Card (rev 03)


Not sure what any of this means. And if it is compatible I have no drivers/installation disk =/ . Many thanks for the help.

---

### Post by petervk on 2009-02-04
Found this:
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D8010)

Not a good card for linux support. The above link shows how to install ndiswrapper which may make the card usuable. What ndiswrapper does is load the windows driver for the device into linux and uses that. It's a 2nd rate way of doing things but it sometimes works.

I'd recommend a different wireless card for best results. You can try the link above if you like. If you get stuck, repost here.

---

