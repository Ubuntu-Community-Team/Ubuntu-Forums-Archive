---
title: "connecting to University Wireless"
date: 2007-06-06
forum: Networking &amp; Wireless
---

### Post by stevodude on 2007-06-06
Laptop: asus z7100a
Intel centrino with 2200bg, which detects fine and does everything it should, including the asus HW button functions...

SSID: found when doing a scan, and also signal strength.

NOw I have the settings for windows as the following:

Network Authentication: WPA
Data Encription: TKIP
EAP type: Protected EAP (PEAP)
	Unticked authenticate as computer
	Unticked authenticate as guest
No Validate server certificate required
Secured Password (EAP-MSCHAP V2)
unticked use my windows logon name

now in windows this brings up a window with:

User Name
Password
Logon domain

All I enter is username & password and I connect fine.

I have Ubuntu 7.04 & wap-suplicant & kwlan
Kwlan gives me all the configuration that is the same as in windows with:
authentication: WPA2-Enterprise (EAP)
Encryption: TKIP
EAP method: PEAP
Identity: username I assume
password: password of course.

now that should be all I need, but never passes the authentication in the WPAlog I get:
date/time stamp: Trying to associate with/mac addess/ (SSID='SSID' freq=0 MHz)
date/time stamp: Authentication with 00:00:00:00:00:00 timed out.
repeat forever...

Is there something I'm missing?

I tried WPA-Enterprice (eap), and then eap method mschapv2 in various combinations, but still no connection.

please help if you can...

maybe the encription is not being passed to a radius server somewhere on the network or something?...

---

### Post by meng on 2007-06-06
Noted the messaged: SSID='SSID' freq=0 MHz
Is SSID really the SSID of the network? Or did you change names to protect the innocent?
I have to admit I've never had luck with Kubuntu and wireless. Now Ubuntu and wireless is a different story, that has always seemed to work great. Go figure, it makes no sense to me.

---

### Post by stevodude on 2007-06-06
yea ssid is not the real ssid, that shows up correctly, and is configured for the correct ssid.

This is with ubuntu, not kubuntu. I have all the WPA tools installed, and couldn't work out how to enter the correct info into ~/wpa-suplicant.conf file, or whatever it was called. So I found kwlan wich has a wpa gui configurator, which made it easy to enter the right info for the wpa config, but still no connection.

cheers, stevo.

---

### Post by meng on 2007-06-06
Ah - my own experience with Ubuntu 7.04 was that I did not need to install anything extra to connect using WPA encryption. The nm-applet was sufficient to connect to the network.

---

### Post by Atomic Dog on 2007-06-06
> **meng said:**
> Ah - my own experience with Ubuntu 7.04 was that I did not need to install anything extra to connect using WPA encryption. The nm-applet was sufficient to connect to the network.

Ditto here.  It worked as well as Windows wireless manager right out of the box :o

Yes that IS a compliment.

---

