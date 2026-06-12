---
title: "Getting a Mac to connect to the internet through Ubuntu?"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by .Danny on 2006-08-30
Ok this is what I'm trying to do. I have a PC, which is connected to the internet via eth0 and pppoe. I'd like to get my Mac to connect to the internet through this PC through a Wireless I think it's called Ad-Hoc or something? Where just 2 normal wireless cards connect to each other.

The one on my Mac is the built in AirPort thing (it's a iBook), the one on my PC is a Netgear WG111v2 connected via USB.

I went through this guide, [http://www.ubuntuforums.org/showthread.php?t=212365](http://www.ubuntuforums.org/showthread.php?t=212365) and finished all steps. Then I open Networking, select wlan0 and go to Properties. I can see the network there fine. Then I select it, write in my password and click ok. And then ok again in the Network window. However it doesn't seem to work.

What other steps do I need to do to make this work?

---

### Post by spd106 on 2006-08-30
Have you set the card into ad-hoc mode?
The command should be something like **sudo iwconfig wlan0 mode ad-hoc**. Check it has worked with **sudo iwconfig wlan0**. Then it should be ok to configure through network-admin gui.

---

### Post by .Danny on 2006-08-31
It seems to connect now if I'm reading it right. However I still have no idea how to 'see' the iBook on Ubuntu or how to see Ubuntu on the iBook. What do I have to do to let the iBook use Ubuntu's internet connection?

[edit] Ok I got it working now. Followed the guide here [http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

---

