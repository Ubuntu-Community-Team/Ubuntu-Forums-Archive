---
title: "Unable to access encrypted wifi"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by newbiefromwindows on 2007-07-20
I have a wifi router that was originally set up using windows. I can detect the network fine, but when I try to connect it does not accept the 128 Bit web encryption passphrase. It tries to connect and then it askes for the passphrase again.I have the password, saved from when the network was set up, so I am almost positive that it is right.

This is what I have saved from the original set up:

> 
Wireless Network Settings

Print this document and store it in a safe place for future reference.  You may need these settings to add additional computers and devices to your network.

Wireless Settings
Network Name (SSID):  my initials
Network Key (WEP/WPA Key):  (right here on my computer)
Key Provided Automatically (802.1x): 0
Network Authentication Type: WPAPSK
Data Encryption Type: TKIP
Connection Type: ESS
Key Index: 

To enable File and Printer Sharing on this computer, run the Network Setup Wizard.
To set up your Internet connection, follow the instructions from your Internet Service Provider (ISP).


Anybody have any ideas?

---

### Post by jml on 2007-07-20
First, was this card able to connect to your encrypted router in another OS, say, Windows?  

Second temporarily turn off encryption on your router.  If you can connect that way, you know that Linux recognizes your card and its just a matter of configuration.  If not, then you will first have to get the hardware sorted out.  What is the chipset of the wireless card that you are using.  

Third, can you clarify what encryption protocol you are using?  WEP, WPA, WPA2.  The output you submitted lists both WEP and WPA.  You can only run one at a time.  Another wrinkle if you are using WEP, the passphrase can be written either in ASCII, or hexadecimal.  Both the router and the computer's wireless card have to be set up the same way, either both using ASCII, or both using hexadecimal.

Just a few thoughts to get you started.

Joe

---

### Post by newbiefromwindows on 2007-07-20
I can access the wifi from the same computer when I boot in Windows. It is WEP I checked in Windows where it tells me. This may be a stupid question, but can a router run two wifi connections? If I set up a wifi connection using ubuntu will the other wifi still be there?

---

