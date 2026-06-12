---
title: "Wireless card refuses to connect after upgrade to Hardy Heron"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by Strfie89 on 2008-05-18
Okay, first of all, after a while on IRC, I found a lot of info on my wireless card. On this page ([http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)) I find that this (Belkin 54g Wireless G Desktop Card (F5D7000) Rev5000) is my wireless card's exact model (pciid: 1113:1211). The entry states that the user could not make the card work.

The closest match on this page ([https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin)), F5D7000 Revision 5100, states that it uses the madwifi driver - and works perfectly out of the box. Well, my wireless card DID work perfectly out of the box when I first installed Ubuntu (version 7.04 at the time). While the eventual upgrade to 7.10 went without any problems, the upgrade to 8.04 pretty much crippled a number of things.

In despair I resorted to an 8.04 Live CD to reinstall the OS clean (I had a number of programs installed, I was certain there were package conflicts), and had it format my ext3 partition prior to the install. Afterward, however, I booted to the 7.04 Live CD and noticed the the most recent version of the nm-applet (0.6) was being used - which it shouldn't be, since I'm running the OS from the 7.04 CD. I conclude that the Live CD was pulling information from my installed copy, creating conflicts and not completely erasing the detrius.

Note in the second paragraph - "uses the madwifi driver". In the Synaptic Package Manager, a search for said driver turns up "linux-restricted-modules-2.6.24-16-generic", which mentions "madwifi (Atheros)" as being "included".

A search for "wireless" turns up the following packages:

jockey-common
jockey-gtk
libiw29
libopenobex1
linux-wlan-ng (which is not installed)
ndiswrapper-common
ndiswrapper-utils-1.9
pcmciautils
wireless-tools
wpa supplicant

I should note at this point that a single left click on nm-applet gives a list of options, including my wireless network - "Barlow-Network" and a bar indicating a signal strength at around 30%. The strength should not be an issue, as the card has always worked with a weak signal (even in Windows XP), and nothing has changed that would affect its strength (i.e., moving the computer, furniture, etc.). (I cannot test in Windows, by the way - XP was on a hard drive that has since died; Ubuntu was installed alongside Windows ME on a used hard drive I acquired afterward; ME has refused to cooperate with the driver from day one.)

I have been through a number of entries listed on this page ([https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)), but the information, to put it simply, is overwhelming; I really don't know where to begin, and some of the pages lead me into a dead end because I get different results*, or because the pages contain outdated information. I would REALLY aprreciate it if someone could try to take me by the hand and offer other suggestions based on what I have said here. Please help me fix this problem.

* For example, on this page ([https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)), iwconfig is mentioned, but I get a different output (which I can post later; I'm not at that computer at the moment.).

---

### Post by nicedude on 2008-05-18
Hey man I don't have your card here but I can give you some insight to what your problem might be related to, if I am right it is related to what my card suffered from. I have a laptop with AR5007 Atheros chipset wifi which uses the madwifi driver as well, In Gutsy I just had to install the correct madwifi and my card worked fine but when I moved to Hardy I found that the linux-restricted-modules which include drivers for the products below were my main problem.

linux-restricted-modules
Currently the following modules are included:
 - madwifi (Atheros)
 - fglrx (ATI)
 - nvidia
 - fcdsl, fcdsl2, fcdslsl, fcdslslusb, fcdslusb, fcdslusb2, fcdslusba,
   fcpci, fcusb, fwlanusb, fxusb (AVM ISDN)
 - ltmodem (Winmodem)

The madwifi module they include for ease of use did not work for my card and was screwing up my wifi. To fix this I had 2 options ( and so do you if it is causing your problem ) first was to blacklist the drivers that were conflicting and then install the correct ones -=OR=- Remove the linux-restricted-modules completely and install drivers for anything that was using this package myself. I chose the second one and ripped the crappy preinstalled modules out along with the restricted driver manager "jockey" at that point I used the correct madwifi drivers for my card and then after that was working I used the Linux Nvidia graphics driver installer available from their site to install the latest Nvidia driver and got my 3D desktop back in action. 

I believe you have the same problem if your card is trying to use the madwifi driver that is installed by default with Hardy. So while I don't know for sure how to fix your problem step by step, I hope this gives you some ideas on what to be looking at.

Hope the info helps steer you to your problem.

nicedude

---

### Post by seantm on 2008-05-19
Another little hardy glitch..

No wireless either. It's basic intelwi-fi card in my T61. It worked seamlessly in Gutsy right out of the box. Now I've upgraded and suddenly no wireless. It sees the card but can not connect. I looked around the forum and tried the following --says it's sleeping...still nothing... Anyone out there with a T-61 who can give me some advice on how to wake it up and connect? TIA.

seantm@techopia:~$ sudo dhclient ath0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:19:7e:93:9a:c9
Sending on   LPF/ath0/00:19:7e:93:9a:c9
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
seantm@techopia:~$

---

