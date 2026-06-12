---
title: "Weird WEP setup at my school - Username/Password thing!"
date: 2006-09-28
forum: Networking &amp; Wireless
---

### Post by daller on 2006-09-28
Hi There,

I'm studying at "Aarhus School of Business" and would like to enable the wireless connection, so that it works on my laptop.

The provided guide is for Windows, but the main setups are as follows:

ESSID: **asbstudent**
Network Authentication: **Open**
Data Encryption: **WEP**

...but I'm not provided with a WEP-key!

In the Windows-guide, I'm asked to mark "The key is provided for me automatically"

Also, I should mark "Enable IEEE 802.1x authentication for this network"

EAN type: **Protected EAP (PEAP)**
Authentication Method: **Secured Password (EAP-MSCHAP v2)**
...and "**Enable Fast Reconnect**" should be marked!

Now I should enter the login information:

Username: **DS12345**
Password: ************
Domain: **asb**

What type of connection is this? - And how do I set it up?

---

### Post by shat on 2006-09-28
Maybe they meant WPA?  I thought PEAP was a WPA thing.........

---

### Post by Buffalo Soldier on 2006-09-29
This is just a wild guess. If you're using the [Network Manager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) applet, left click on the applet and choose "Connect to other wireless network" and you will get something like the attached screenshot. But I'm not sure how to proceed further. My knowledge on secured wifi is very limited. Sorry.

---

### Post by seekyrr on 2006-09-29
I believe you are trying to use PEAP (EAP-MS-CHAPv2) which is 802.1x and uses server Certificates and Client Passwords.

Select WPA Enterprise and put in your info.

Seek.

---

### Post by daller on 2006-09-29
I'm using Kubuntu...

How do I accomplish setting it up?

Any info for /etc/network/interfaces ???

---

### Post by dppowell on 2006-09-29
Download and install Network Manager from the Ubuntu universe repository--the options your school's network wants are configurable from NM's interface. (and it's just a nice app to have for switching between wireless networks.)

---

### Post by aerials on 2006-10-24
My school seems to have the same network settings as daller's, but it won't work with network-manager: When I try to connect to another wireless network and chose WPA Enterprise or WPA2 Enterprise so that I can select PEAP and enter username and password provided by my school, network-manager won't connect to the SSID I wish: The daemon log tells me, that nm skips that SSID because it doesn't provide WPA/RSN IE. ](*,)

---

