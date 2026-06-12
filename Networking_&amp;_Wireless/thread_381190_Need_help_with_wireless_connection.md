---
title: "Need help with wireless connection"
date: 2007-03-10
forum: Networking &amp; Wireless
---

### Post by sadalmelik57 on 2007-03-10
I have a pentium 2 running Ubuntu Edgy 6.10 which previously would pick up the WiFi signal using a USB Wireless Adapter from Gigafast model WF748-CUI.  This is using the Zydas 1211b driver.  

The signal was weak and had to be within eyesight of the router, so I decided to try a wireless card by Zonet model ZEW1602, with the 3COM driver.  This isn't listed as Linux-friendly, but with the help of a friend in the local Linux Users Group we were able to start the installation of the driver through Wine.  We ran out of time.  The driver is shown in the Wireless Drivers list and the device is shown as present, but so far I can't get a wireless signal and to make it worse now I can't get a signal with the USB Gigafast wireless adapter either!  I don't know what changed there.

Here is the output of my lspci and iwconfig.  Can you get me pointed in the right direction?
The device is listed as Marvell 88w8335 Libertas.  I'm not a newbie, but I'm not that experienced either. :confused: 

l@AOPEN:~$ lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
00:0a.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
00:0b.0 Communication controller: Conexant HCF 56k Data/Fax/Voice/Spkp Modem (rev 08)
00:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 RF/SG AGP
l@AOPEN:~$ 
l@AOPEN:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by scrooge_74 on 2007-03-10
You are not suppose to install the drivers using wine, you should be using ndiswrapper

---

### Post by sadalmelik57 on 2007-03-10
Well, you're right.  Thanks for your response.  It just shows you my lack of familiarity.  He installed the original driver .exe package with wine, but then used the drivers that were unpacked and installed them with NDISWrapper.  

Looking back at the command he used it was:
sudo ndiswrapper -i mrv8335x.inf

The mrv8335x.inf driver shows up in the Wireless Drivers list and says that the device is present, which I think indicates it can see the hardware.

Thanks for looking!

---

### Post by cherokee on 2007-03-10
Hi sadalemlik57,

The info is out there in the wiki an google ubuntu here is some links that will take you through the copy and paste


[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I hope you can find this link and The steps to follow how to.

 [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)



flint_dude

---

### Post by sadalmelik57 on 2007-03-11
Thanks.  My driver is not shown in the lists on the first link.  Mine is CRGP_10075.  The second link does get me to some documentation I haven't seen yet so I'm hoping I'll be able to pick it up and run with it from there.  Thanks for the links.

---

