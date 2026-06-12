---
title: "Connect to WEP-protected Wireless Network"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by niklasfischer on 2006-12-11
Hi!

I'm trying to connect to my WEP-protected Wireless Network at home.

WIRELESS NETWORK SETTINGS
-------------------------
SSID: NETGEAR
CHANNEL: 11
Shared
64-bits key hexadecimal using first of four keys generated at the router.

Wirless Network Card
--------------------
D-Link DWL-510 (RTL8180)

PROBLEM
-------
My network card is detected and running and when I use the Network tool in System->Administration I can set my eeid and password and everything seems to work but Idon't get an IP-address and the card cannot find any AP.

I have tryed NetworkManager but it dosen't show my wireless connection and when I doubleclick the nm-icon nothings happen (some forums tells me to do so and then choose add connection).

I then tried WIFI-radar and it shows the wireless connection but I can't do anything with it.

I then tried another graphical tool that I don't remember the nam for but that tool shows me the wireless connection and it shows me the signal strength which is good but I still don't get an IP-address and therefore I cannot connect to Internet for example. 

I'm stuck and I cannot find any solution to my problem at any forum. From what I can tell I don't have to use any wrapper for windows driver or wap_Supplicant with my settings and hardare...

For whats it worth I can use the card perfectly in Windows so there is no router failure or other hardware failure...

Can anybody help me?

---

### Post by FrodoB on 2006-12-11
For purposes of debugging remove the WEP from the wireless router and the Ubuntu side and see if you can connect.  If so go generate new WEP keys and put them into both router and Ubuntu.

[http://www.andrewscompanies.com/tools/wep.asp](http://www.andrewscompanies.com/tools/wep.asp)

Normally HEX keys are the sure way to go, but if you want to use ASCII then start the key with "s:" to denote that an ASCII key follows.

Also check the contents of /etc/network/interfaces to make sure that what you entered in the Networking menu matches what you have in your router:

sudo gedit /etc/networking/interfaces

---

