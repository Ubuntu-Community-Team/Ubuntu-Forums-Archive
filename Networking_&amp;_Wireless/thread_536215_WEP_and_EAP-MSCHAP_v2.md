---
title: "WEP and EAP-MSCHAP v2"
date: 2007-08-27
forum: Networking &amp; Wireless
---

### Post by MR Bacardi on 2007-08-27
My girlfriend's school has a network with WEP encryption, EAP-MSCHAP v2 authentication (username and password prompt in Windows).
She is using Ubuntu at her laptop, but she has not been able to connect to their network.
I have tried a setup like (in /etc/interfaces/networking) :
auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-eap PEAP
wpa-key-mgmt WPA-EAP
wpa-identity <your_identity>
wpa-password <your_password>

Which I found in [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
However, she still can't access the network.

She is thinking of changing back to Windows, but I can not believe if it is not possible to setup Ubuntu so it is able to connect.
Therefore I am hoping for some help from you guys.
The best solution would be one I can setup at home, so she can just log right on to the network.
Unfortunately the school is too far away for me to just go there and try it out myself.

---

### Post by MR Bacardi on 2007-08-28
Any suggestions are still welcome...

---

### Post by will71110 on 2007-08-28
If they are using WEP the WPA will not work.

Is the computer able to see the wireless network(SSID)?

---

### Post by wieman01 on 2007-08-28
First off, does the card work at all?
> sudo iwlist scan
This is the right script for you:
> auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid <your_essid>
wpa-ap-scan 1
wpa-eap TTLS
wpa-key-mgmt [COLOR="Red"]IEEE8021X[/COLOR]
wpa-anonymous-identity <anonymous_identity>
wpa-identity <your_identity>
wpa-password <your_password>
wpa-phase2 auth=[COLOR="Red"]MSCHAPV2[/COLOR]
IEEE8021X refers to WEP.

Does Network Manager not support MSCHAPV2?

---

### Post by MR Bacardi on 2007-08-29
> **will71110 said:**
> 
Is the computer able to see the wireless network(SSID)?
Yes, the network is visible, but only WEP 128-bit passphrase, WEP 64/128-bit HEX and ASCII can be chosen. According to network administrators there is no "main" password.

> **wieman01 said:**
> First off, does the card work at all?

Does Network Manager not support MSCHAPV2?

The card has no problems connecting to my wireless network at home (WPA2 encrypted)

I have not been able to find anything on MSCHAPV2 in the GUI.

I will try the script you posted when possible :)

---

### Post by wieman01 on 2007-08-29
Alternatively, try WICD. It might support MSCHAPV2:

[http://wicd.sourceforge.net/features.php]("http://wicd.sourceforge.net/features.php")

---

