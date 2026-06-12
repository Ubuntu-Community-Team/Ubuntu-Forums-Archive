---
title: "Wirless DWL-G650+ on nx6110"
date: 2007-01-24
forum: Networking &amp; Wireless
---

### Post by hokah on 2007-01-24
Hi
Im little confused becouse Im not Linux Pro and I dont understand this:

I have laptop computer 

HP nx6110 with DWL-G650+ Wireless card

My experience with Linux Installation:

Kubuntu 6.10 Works great and wireless card working just as it should
Ubuntu 6.06 and 6.10 impossible to install Live CD hangs during installation process
Suse 10.2 Detects DWL-G650+ but doesnt work

Whats is about that one distro supports wirless card and another one doesnt it is very confusing as I have spent so many h to install onw its working.

regards
Peter

---

### Post by VorDesigns on 2007-01-24
Hi, 
I have had similar distractions for the last three weeks trying to get my D-Link DWW-G650 card working until today.
I walked throough a ton of posts here and this lists all the things I did and my opinion about what ultimately worked.

My Interfaces config for ath0
auto ath0
iface ath0 inet dhcp
### Below added as per another thread, didn't help
pre-up ifconfig ath0 up
pre-up ifconfig ath0 down
pre-up ifconfig ath0 up
pre-up wlanconfig ath0 create wlandev wifi0 wlanmode sta
### below added as per another thread, doesn't seem to be
### of much value
wireless-key XXXXXXXXXXXXXXXXXXXXXXXXXX // expunged
wireless-ap 00:00:00:00:00:00  // expunged
wireless-channel 0 // expunged
wireless-essid my_ap_name
wireless-mode managed

While I already had the key, ap MAC, channel, name and mode in hand, it is good to know that you can scan for ap in the area using 
iwlist scanning // for a list of other capabilities, just type iwlist.

None of the above seems to have done any good but I didn't want to remove any of it since I don't know if it didn't do some of the necessary tasks needed to ultimately connect.

Finally, I do the following ever time I boot
From a terminal window
sudo iwconfig ath0 key XXXXXXXXXXXXXXXXXXXXXXXXXX // my key
sudo iwpriv ath0 authmode 2 // sudo may not be necessary since it was just entered.
sudo dhclient ath0 // ibid.

Viola!  the blinky lights go from alternating (zombie mode) to synchronous (linked mode).
I distilled the commands above from the MadWiFi documentation bouncing around between turtle (newbie) and WEP and troubleshooting and so forth

I'm running Dapper Drake 6.06 LTS.

Some time in the future, I will see if I can figure out how to get this to load via script but I'm geek enough to bring the interface up the rest of the way manually and it's only a minor annoyance

What is clear to me is that the System networking control panel in Dapper doesn't work very well for wireless and I also note that MadWiFi on Dapper doesn't seem to be completely implemented as some of the commands that I was lead to believe should produce a result through a what am I talking about error.

Anyway, I want to thank all of the people who use DWL-G650 in their posts because it gave me lots of things to try and the MadWiFi folks for their documentation although I find it novel that they don't tell you where their application is usually installed and then expect you to know where the /scripts directory for the installed application is when the document was supposed to have been written for a turtle.

I did try KUbuntu (Blue) for about two hours before going back Ubuntu (Brown) after having the same luck with only marginally more informative GUI information "Connection failed".

---

### Post by tturrisi on 2007-01-24
the dlink dwl650g has been manufactured with several different chipsets, it depends on the version # of the card.  Knowing the version one can then determine the chipset and then the exact driver needed.
[http://linux-wless.passys.nl/query_part.php?brandname=D-Link](http://linux-wless.passys.nl/query_part.php?brandname=D-Link)

---

### Post by mimsmall on 2007-02-02
For what it's worth my Dlink G650 with Atheros chipset just worked after I set up Network manager. My laptop is a HP pavilion ze4400. I'm retired and just use my computer for banking, email and entertainment. I only wifi at public hot spots, library, courthouse, and church, the rest of my computer time is dial-up.

Family and friends consider it great fun:lolflag:  to send me videos and slideshows.

---

