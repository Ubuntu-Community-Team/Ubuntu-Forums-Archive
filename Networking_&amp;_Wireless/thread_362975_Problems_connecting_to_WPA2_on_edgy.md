---
title: "Problems connecting to WPA2 on edgy"
date: 2007-02-16
forum: Networking &amp; Wireless
---

### Post by raffij on 2007-02-16
Hi,

I just installed Edgy Eft on my laptop. I'm trying to connect it to my wireless AP using WPA2. I am able to connect to the router using Windows on this box and others.

At first I couldn't get any connectivity (not a suitable AP or some such) so I turned on broadcasting on my AP as a test.

my wpa_supplicant.conf file looks like this...

network={
	ssid="myssid"
	scan_ssid=1
	proto=RSN
	key_mgmt=WPA-PSK
	pairwise=CCMP
	group=CCMP
	#psk="mypassword"
	psk=mykeyishere
}

sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext

Trying to associate with 00:15:e9:7f:b7:07 (SSID='myssid' freq=0 MHz)
Associated with 00:15:e9:7f:b7:07
WPA: Key negotiation completed with 00:15:e9:7f:b7:07 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-CONNECTED - Connection to 00:15:e9:7f:b7:07 completed (reauth) [id=0 id_str=]
WPA: Key negotiation completed with 00:15:e9:7f:b7:07 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:15:e9:7f:b7:07 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:15:e9:7f:b7:07 [PTK=CCMP GTK=CCMP]
WPA: Key negotiation completed with 00:15:e9:7f:b7:07 [PTK=CCMP GTK=CCMP]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys


This continually repeats. I searched on google and found several articles relating to this but nothing definitive for what worked.


Any ideas? Thanks.

---

### Post by raffij on 2007-02-16
never mind. a reboot helped. go figure.

---

### Post by wieman01 on 2007-02-16
How did you generate the key?

---

