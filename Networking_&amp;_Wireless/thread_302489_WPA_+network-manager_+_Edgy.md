---
title: "WPA +network-manager + Edgy"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by Caderider on 2006-11-18
Help

I am new to linux.  I want to get away from windows but.

I first installed dapper and updated.  My card is USR5410.  I have done so many different things I have lost track.  I have reinstalled several times now and I now have upgraded to edgy. Several posts said Edgy was better but no luck. Ther does not seem to be any basic instructions to get WPA and using Ndiswrapper working.  I have ndiswrapper and the windows driver/s installed. 

How do I start wpa with ndiswrapper automaticaly.  I have network-manager installed all I get is 3 wep choices. 

I have a Dell C400 with a pcmcia card on built in WiFi.

---

### Post by MrFSL on 2006-11-18
(FOR THE LINUX WIRELESS NEWBIE)

Step one to wireless network success for Ubuntu is to get your network running without added security features. (i.e. no wep, no wpa, no firewalls, etc.)

Once that is done we add our layers of protection one at a time, layering them one after the other and testing the network as we go.

When you get to adding wpa I suggest you read the wireless guide in the Ubuntu Community help documentation and also google yourself some info on ***wpa_supplicant***

Most often when helping others with Debian and Redhat networking issues in the past I found that the problem was not at all what they suspected. By building your network up like this (although blatently yet temporarily vulnerable) you might just fix your problem, or identify the real culprit.

MrFSL

---

