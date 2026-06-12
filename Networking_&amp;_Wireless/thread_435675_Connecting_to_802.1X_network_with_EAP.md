---
title: "Connecting to 802.1X network with EAP"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Diversion on 2007-05-07
I'm trying to connect to my school network.
My school network requires me to log in using a username and password.
Network card works fine because I can connect to my home network which uses WPA.
I'm using Network-Manager-gnome to connect to my home network.

The ideal sollution would be for me to select my school network using the network-manager, which then loads the right configuration file for the login using the WPA-suplicant(which is allready installed).

School supplied me with a sample config file to add to my wpa_supplicant.conf :

network={
	ssid="hu-eduroam"
    	key_mgmt=IEEE8021X
    	eap=TTLS
    	identity="login"
    	password="password"
    	phase2="auth=PAP"
}

but I can't seem to get it working the right way.
My other concern is, when this is working, will it affect my connection at home?

Any help would be greatly appreciated!

---

