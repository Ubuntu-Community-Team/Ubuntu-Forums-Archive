---
title: "Wireless with PEAP and MSCHAP2"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by ElSnotto on 2007-01-22
Im trying to setup my install of Edgy on the wireless network. Our wireless network administrator has been kind enough to give me the required settings.

Can anyone help me with what to do next.

 

SSID:
mynet

Wireless Mode:
Infrastructure (same as ESSID)

Authentication:
WPA2

Data Encryption/Cipher:
AES (CCMP) or TKIP

IEEE 802.1X Method:
PEAP

EAP Type:
EAP-MSCHAPv2

Fast Reconnect:
Enabled

Validate Certificate:
Disabled

Frequency:
802.11a/b/g (5.0GHz & 2.4GHz)

---

### Post by spd106 on 2007-01-23
See the sticky at the top of the networking/wireless sub-forum for a basic outline with examples, click [here]("http://ubuntuforums.org/showthread.php?t=318539")

---

### Post by rorzer on 2007-03-15
Any Luck?  My uni has the same setup.  I've been looking at the wpa_supplicant documentation here: [http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/README?rev=HEAD&content-type=text/plain)

And I'm hoping to set up a gui interface with wicd manager [http://compwiz18.blackhole.cx/wicd/wb](http://compwiz18.blackhole.cx/wicd/wb) which seems to be more configurable for out-of-the-ordinary security setups than network manager is at the moment.

I'll post here again to let you know what works.

Rorzer

---

