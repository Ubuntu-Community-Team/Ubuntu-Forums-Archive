---
title: "Wicd Settings For Feisty Fawn?"
date: 2007-06-25
forum: Networking &amp; Wireless
---

### Post by monkfishbandana on 2007-06-25
I have always used WPA protection on my wireless connection at home. It works with Windows XP, but I recently downgraded it to WEP-64bit (I know, bad choice) to not only enable my Nintendo DS to access the internet, but more importantly ;) to allow Ubuntu to use the internet. The DS would lose connection regardless after about 2 minutes, but Ubuntu worked fine. I worried about security so I put the modem back to WPA protection.

After a long, long, long, long, *long* time trying to get WPA working with 7.04 (FF), I decided to try again with Wcip. I need help though:

I'm 99% sure that I am using a Broadcom module (Belkin Wireless Card [PCI]), and I have already tried ndiswrapper.

I open Wcip, enter some stuff, and then comes the encryption...

I am given WPA 1/2, and although I am very computer literate I have no idea what the hell this is. My modem (also Belkin) gives me the following options:

WPA/WPA2-Personal (PSK)
WPA/WPA2-Enterprise (RADIUS)

I have selected PSK, because RADIUS gives me some forms I don't know how to use.

WPA-PSK
WPA2-PSK
WPA-PSK + WPA2-PSK

I have selected WPA-PSK, because it is default (and because I don't know the difference between them, although I am guessing the dual one is more secure, as is the WPA2).

TKIP
AES
TKIP + AES

I have selected TKIP, because it is default. So my settings are:

**Security Mode:** WPA/WPA2-Personal (PSK)
**Authentication:** WPA-PSK
**Encryption Technique:** TKIP

When I go into Wcip and select *Encryption: WPA 1/2*, I enter the PSK and it hangs on "Obtaining IP Address".

I have been into preferences and entered the correct Wireless Interface (eth2 according to iwconfig) and selected "broadcom" as the driver. I have also tried "ndiswrapper" as the driver.

The internet worked fine before with Network Manager utilising WEP-64bit security.

Unfortunately, to install Wcip I also uninstalled network-manager and network-manager-gnome, so they don't work properly now. Please no-one suggest (as I have previously seen) Synaptic because, obviously, I cannot access the internet.

So, what I am gratefully asking for is for somebody to possibly point me in the right direction for:

[LIST=1]
[*]Re-installing 'network-manager' and it's affiliated packages, or if possible (and more ideally),
[*]Suggest optimal settings for Wcip.
[/LIST]

Thank you very much for your time, it's a problem I need to resolve (due to extreme lack of sleep).

---

### Post by ugm6hr on 2007-06-25
> **monkfishbandana said:**
> Re-installing 'network-manager' and it's affiliated packages, or if possible (and more ideally),
Suggest optimal settings for Wcip.

If you haven't deleted your archives, Network Manager will still be stored on your harddrive, so Synaptic should actually install it without internet access (have a look in /var/cache/apt/archives for network-manager and network-manager-gnome).

If you want to persevere with Wicd - I would suggest trying v1.2.9 testing (which I found a lot better - and more stable - than v1.2.7 with Feisty).
Then try resetting your wireless router to WEP (as you did with Network Manager), and see if Wicd will connect.  That will at least confirm that it works for your system.  If so - the only other issue could be wpa-supplicant and it's interaction with your chipset.

Then post the output of
```
lspci
```
so that you can confirm the chipset used.  That may give a clue as to whether WPA is possible, and how best to go about getting it to work (and which wpa-supplicant driver to try).

A screenshot of the WIcd settings for your wifi network would be useful too (the one with the SSID, Automatically connect to this network, Advanced settings etc).  This should detail your DHCP / IP settings, and also confirm whether the network is correctly detected as WPA/WEP.

Also - I know it seems obvious, but have you restarted after uninstalling Network Manager?

EDIT:
This suggests you need to use wext (not ndiswrapper/broadcom) as wpa-supplicant driver in preferences:
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,wpa/)

---

### Post by letmein on 2007-07-31
I have the exact same issue as the original post, except my chipset being 

> 03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)


Im trying to get WAP to work and as original post...just hangs on "obtaining IP address", im using wicd version 1.3.1.

[IMG]http://www.freeimagehost.ro/viewer.php?file=Screenshot-Wicd Manager.png[/IMG][http://www.freeimagehost.ro/viewer.php?file=Screenshot-Wicd Manager.png]("http://www.freeimagehost.ro/viewer.php?file=Screenshot-Wicd Manager.png")

---

### Post by ugm6hr on 2007-07-31
> **letmein said:**
> I have the exact same issue as the original post, except my chipset being 

Im trying to get WAP to work and as original post...just hangs on "obtaining IP address", im using wicd version 1.3.1.


I'm on v1.3.1 now too - with Atheros5005G.  I believe 5212 is supported by madwifi - so it should work.  

Things to check:
> Preferences: 
WPA suplicant *wext*
Wireless *ath0*

Then try WPA password with or without "" quotation marks around it.  Make sure you select WPA1/2 for password type.  Double-check you've got password right too!

---

### Post by letmein on 2007-08-01
Well, I got my WPA up and running, but its conditional.  

Condition #1: Only works on reboot
Condition #2: I cant change networks and then reconnect to wpa (see condition #1)
Condition #3: WPA has to be broadcasting its SSID

Anyone know why? It would be nice to be able to use wicd or wifi-radar or knetworkmanager....or anything, to be able to switch from a wired network to a wireless one and vice versa, without having to restart each time.

---

### Post by ugm6hr on 2007-08-01
> **letmein said:**
> Well, I got my WPA up and running, but its conditional.  

Condition #1: Only works on reboot
Condition #2: I cant change networks and then reconnect to wpa (see condition #1)
Condition #3: WPA has to be broadcasting its SSID

Anyone know why? It would be nice to be able to use wicd or wifi-radar or knetworkmanager....or anything, to be able to switch from a wired network to a wireless one and vice versa, without having to restart each time.

Interesting that mine seems only to work with Condition #2 too.... I don't think I'd ever tried swapping connections "live" before.  

I know that the developers are working on automatic connect to wired whenever plugged in in v1.3.2/1.3.3 (currently testing).  Fingers crossed [-o<

Perhaps you might want to give the testing versions a try, since this feature is important to you....

---

