---
title: "Can anyone help a newbie???"
date: 2007-12-04
forum: Networking &amp; Wireless
---

### Post by Joe.Kent on 2007-12-04
I have a dell 600 laptop with a 1ghz processor I'm trying to install GOS or Ubuntu 7.10. I can't get my belkin F5D7010 wireless card to work with either of these. Where do I need to find the driver for this and where do I get ndiswrapper? Thank you in advance, and I hope these aren't stupid questions, I'm just trying to get away from MS. I will have Ubuntu 7.10 on one computer, and GOS on my daughters computer, she is 5 and I think its more suitable on hers. thanks again...

---

### Post by MariusSilverwolf on 2007-12-04
Joe,

You should be able to get most of the support you need by following this How-To, as Dell lists the 600 as using a Broadcom 4311 chipset for the wireless network card: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

G'luck to ya!

---

### Post by Junglizer on 2007-12-04
Well its a Belkin, so you may actually have legit drivers and not have to use NDIS at all, which would be nice. To start we need to figure out what chipset the card is, plug it in and run: ```
root@system~# lspci
```
This will out put a list of what manufactures and junk the stuff on the board and expansion slots are. If you can post the output of that command it will give us a good place to start.

---

### Post by Junglizer on 2007-12-04
> **MariusSilverwolf said:**
> Joe,

You should be able to get most of the support you need by following this How-To, as Dell lists the 600 as using a Broadcom 4311 chipset for the wireless network card: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29)

G'luck to ya!

I would have to dissuade you from using the how-to in that link as I feel that it would not work very well for you. The device in question in that article is a mini-PCI card Broadcom built-in. Not really what you've got even if it is a similar laptop, however if you find that  your Belkin card has that same Broadcom chipset then it may be helpful.

---

### Post by Joe.Kent on 2007-12-04
> **Junglizer said:**
> Well its a Belkin, so you may actually have legit drivers and not have to use NDIS at all, which would be nice. To start we need to figure out what chipset the card is, plug it in and run: ```
root@system~# lspci
```
This will out put a list of what manufactures and junk the stuff on the board and expansion slots are. If you can post the output of that command it will give us a good place to start.



Here goes...  Can anyone tell me how to copy next time... tried everything... cp... copy, right click...nothing worked...

00:00.0 host bridge: Intel Corp 440bx/zx/dx - 82443bx/zx/dx/host bridge (rev 03)
00:01.0 PCI bridge: Intel Corp 440bx/zx/dx - 82443bx/zx/dx/ AGP bridge (rev 03)
00:03.0 CardBus bridge: texas ins PCI420 PC card Cardbus Controller
00:03.1 Cardbus bridge: tx inst PCI420 PC card Cardbus Controller
00:07.0 Bridge: Intel Corp 82371AB/EB/MBPIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corp 82371AB/EB/MBPIIX4 IDE (rev 01)
00:07.2 USB interface: Intel Corp 82371AB/EB/MBPIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corp 82371AB/EB/MBPIIX4 ACPI (rev 03)
00:08.0 Multimedia audio Controller: ESS Technology ES1983S Meastro-3i PCI audio accelerator (rev10)
00:10.0 Ethernet controller: 3com Corp 3c556 Hurricane Cardbus [Cyclone] (rev 10)
00:10.1 Communication Controller: 3 com corp Mini PCI 56k winmodem (rev 10)
01:00.0 VGA  compatible controller: ATI tech inc rage mobility M# AGP 2x (rev 02)
06:00.0 Network controller: broadcom corp BCM4318 [Airforce one 54g] 802.11g wireless LAN controller (rev 02)


I hope that is what you needed... it was a pain to type all of that...

---

### Post by Junglizer on 2007-12-05
> **Joe.Kent said:**
> 
06:00.0 Network controller: broadcom corp BCM4318 [Airforce one 54g] 802.11g wireless LAN controller (rev 02)


Was all you needed, and for the record, to copy and paste from the terminal you simply highlight the text and right-click to paste it.

Looks like you do indeed have a Broadcom chipped card. So that guide MariusSilverwolf linked you too may be of help to you now. However in reading that guide I personally found it to be the biggest POS and such a run around. I would recommend you start around step # 4 (read the previous steps but I don't think they'll apply to you) as step 4 starts with the download/install of NDISWrapper. Once you have it installed I would recommend reading the manual for it:
```
man ndiswrapper
``` to see specifically how to operate it. If you have the Windows install CD for your wireless card, pop it in, as you'll need a windows driver file from this, which is how ndiswrapper works.  I believe you'll want a .inf file, but its been a while since I've used NDIS, the manual should say what files to look for. What you can see in step 5 is that they have one of those "InstallShield" compressed cabinet installer files. If you have this instead of a folder in which you have just the driver files on the CD, the process is the same, you'll just be looking for different files.

---

### Post by Joe.Kent on 2007-12-05
Thank you guys alot. I will try this later today and see what I can come up with.

---

### Post by rustybronco on 2007-12-05
I have the pci version of this desktop card (Dynex) and in 7.10 it works ootb by enabling the restricted driver, the linked card has a bcm4318 chipset, it should work without ndis.
[http://ubuntuhcl.org/pub/reviews.php?product_id=412](http://ubuntuhcl.org/pub/reviews.php?product_id=412)
I have the 32 bit install of 7.10

---

### Post by Joe.Kent on 2007-12-05
> **rustybronco said:**
> I have the pci version of this desktop card (Dynex) and in 7.10 it works ootb by enabling the restricted driver, the linked card has a bcm4318 chipset, it should work without ndis.
[http://ubuntuhcl.org/pub/reviews.php?product_id=412](http://ubuntuhcl.org/pub/reviews.php?product_id=412)
I have the 32 bit install of 7.10


Can you tell me how to do that? I'm really this new to linux. I have the driver loaded through ndiswrapper, but it says hardware not found. Thanks in advance.

---

### Post by rustybronco on 2007-12-05
it was a fresh install.

[http://ubuntuforums.org/showthread.php?t=595442&highlight=dynex](http://ubuntuforums.org/showthread.php?t=595442&highlight=dynex)

Easy way to check if it works, fire up the live cd and try it.

---

### Post by Joe.Kent on 2007-12-06
I have a new question for you guys... I ditched GOS and downloaded the iso for 7.10... but when I try to install it hangs up at 15% installing systems, detecting file systems. I even tried to download from another source and burn a new iso.... any tips?

---

### Post by 449 on 2007-12-06
> **Joe.Kent said:**
> I have a new question for you guys... I ditched GOS and downloaded the iso for 7.10... but when I try to install it hangs up at 15% installing systems, detecting file systems. I even tried to download from another source and burn a new iso.... any tips?

Are you installing on an external HDD?

---

### Post by Joe.Kent on 2007-12-07
Ok.... good news, after burning yet the fourth iso image, and this time I chose the alternative cd, I have 7.10 installed and the lights on the wireless card are on. Now I just have to figure(configure, weird those two words have so much in common) it and use the wireless. Also, I'm going to try and figure out how to tether my blackjack to it and use it as a modem.

---

