---
title: "Linksys Wireless-G..."
date: 2005-07-18
forum: Networking &amp; Wireless
---

### Post by Declan on 2005-07-18
Hi all,

I purchased the linksys wireless-g card (802.11g), on the advice of the vendor who said that since it was a Cisco product it almost certainly works with linux.
I am using hoary, and I've followed some of the instructions that I've read here and there in the forums (without understanding them).  Including the installation of ndiswrapper, and the installation (as I understood it) of the driver from the cd-rom.  And so on.

It is not working (yet).  I am wondering how to confirm that the computer recognises the presence of the card.  So I tried lspci, but I don't know how to interpret the results....

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device cab3 (rev 05)
0000:00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4347 (rev 01)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4348 (rev 01)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4345 (rev 01)
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4349
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc: Unknown device 434d (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4437
0000:02:06.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)

Do any of these refer to the card?
If not, how to I verify that the computer recognises the effective presence of the card?

Thanks,

Declan

---

### Post by andlinux21 on 2005-07-18
Are you using a Desktop or laptop and is this the only computer using the wireless?

---

### Post by Declan on 2005-07-18
This is a laptop.
I don't understand the second question. This is the only computer using the card.  I don't have dual boot, so I'm not able to test the card on a Windows system.  
The network has another laptop with XP and an internal wireless connection connecting successfully to the network.

The output of iwconfig, incidentally is:

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

The laptop has had some electrical difficulties, and has had to have the motherboard changed. That's what's making me wonder if the card is even being detected.  Unfortunately, I can't decipher the results of lspci.  Linksys is not mentioned... but branding of computer accessories is not always linked to the manufacture of those products, as far as I can see.

Thanks,

Declan

---

