---
title: "Wireless Issue after Fiesty Upgrade"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by gantww on 2007-05-12
Hello all,
I finally upgraded to Fiesty on my wife's laptop late yesterday evening. The upgrade went very slowly (like 4 hours). Everything else worked perfectly, so I don't care about the time too much, but I lost my wireless connection. The environment here consists of a Linksys router with a network name of WilliamGant. The SSID is not broadcast. I'm using WEP with a 128 bit 26 digit key. The Network connection was originally on "lo", but the option wlan0:avahi was also available. However, when I switch to it, it says that it doesn't exist. It's also apparent that the machine is not getting an IP address, so I tried to use a static one. Even setting a static one, you can't reach the router, which leads me to believe that it isn't connecting to the wireless network at all.

Any thoughts?

---

### Post by bscbrit on 2007-05-12
Just to clarify, can you confirm that in System -> Administration ->Networks your wifi card is identified and has the appropriate settings?

How are you 'switching to it'?

What driver were you using under the previous version of Ubuntu?  Have you re-installed it under Feisty?

---

### Post by gantww on 2007-05-12
It doesn't actually identify the card. I don't remember if I installed another driver for it or not. I probably did though. It's a Netgear WG511 card. As for switching to it, I right-clicked on the network connection icon up by the system clock, then went to properties. There is a drop down list there with "lo" and "wlan0:avahi" in it. I selected "wlan0:avahi".

---

### Post by bscbrit on 2007-05-12
I'm trying to locate a good guide to assist you in setting up the wireless network, but the guide/howto that I used to recommend appears to have disappeared during my 4 month absence from this forum.  I'll keep looking for its new address but perhaps in the meantime someone will come along and offer more useful advice.  

Its Saturday evening and I have a wife and family, so I will probably not be back online until tomorrow....

---

### Post by bscbrit on 2007-05-13
Found it !

[https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting](https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting)

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Start at the beginning and keep going until it either solves your problem or you hit a snag, in which case come back here and we will help.

Good Luck

---

### Post by gantww on 2007-05-13
Apparently the upgrade broke my wired and wireless connections. At any rate, lspci is showing:

Network Controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prison Xbow] (rev 01)

My wired card is showing as:
Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

The wired card is built into the machine, and that looks like what I remember from when I installed it. The wireless card is a Netgear WG511, so I'm assuming that the information listed here is chipset-related...?

What strikes me is odd has to do with the network settings dialog. It's showing TWO wireless connections and a wired connection. All three are enabled. I've tried configuring both of the wireless connections to connect to my router, with no success.

Any thoughts?

---

### Post by bscbrit on 2007-05-14
Usually, the wired connection is much easier to set up than the wifi and, once you are connected, the wired network will allow you to download the necessary software to enable the wifi to be configured.  My recommendation is to get the wired network operating and then we can start on the wifi.

The wired network card requires the B44 driver ([http://www.fsf.org/resources/hw/net/wired-ethernet)](http://www.fsf.org/resources/hw/net/wired-ethernet)).  I don't know if this driver is available from the Ubuntu CD or perhaps you have a driver CD that came with the laptop?  However, there is a good chance that you can configure it from System->Administration->Network.  Select the default setting (DHCP) and try to get connectivity.

How are you accessing this forum at the moment - is your laptop dual-boot or are you using another computer?

---

### Post by gantww on 2007-05-14
It's not dual boot, but I am using another computer sitting right beside it. Apparently the driver either isn't installed or isn't working properly, as I can't make a connection using DHCP (or even a static IP). I just tried the link you sent, but I got an error saying it wasn't found.

---

### Post by gantww on 2007-05-14
Could it be related to this issue?

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/105858)

---

### Post by bscbrit on 2007-05-15
Sorry about that, it worked when I tested it, but not now.

Try this:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

---

### Post by gantww on 2007-05-15
I don't know much about wireless, but when I run lshw the wireless card comes up as:

[Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]

I seem to remember someone suggesting that I use NDISWrapper for this. Is that what you would recommend?

Thanks,
Will

---

### Post by gantww on 2007-05-15
Also, I ran the following:

sudo pccardctl ident

and got back:

no product info available

Apparently I'm supposed to edit the /etc/pcmcia/config.opts file. What do I put in there for this card? Is there any easier way to do this?

Will

---

### Post by gantww on 2007-05-15
I wiped and reinstalled from scratch. Wireless works perfectly when attempting to connect to an unsecured network. Screen resolution is horrid, but I've already posted on that one in the general forum.

---

### Post by bscbrit on 2007-05-16
In which case the problem appears to be in the encryption.  If you are using WEP then it should be configurable from System->Administration->Network.  If you are using WPA, make sure that you have wpa-supplicant installed.

---

