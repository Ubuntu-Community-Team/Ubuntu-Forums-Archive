---
title: "No WPA2 with an Intel 2100bg"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by giruzz on 2007-01-22
Hi Guys,

I spent afternoon and evening trying to establish a connection between my Netgear DG834g and my Intel 2100 using WPA2.

I can connect without any problems using WPA or WEP but when I'm trying to connect using WPA2 the wifi card doesn't work...

I don't know why...

this configuration doesn't work:

```
network={
 	ssid="The_house_of_love"
 	scan_ssid=1
	proto=RSN
 	key_mgmt=WPA-PSK
 	pairwise=TKIP
	group=TKIP
 	psk=#deleted_for_security_reasons#
}
```

This one works (only with WPA), 

```
network={
 	ssid="The_house_of_love"
 	scan_ssid=1
	proto=RSN WPA
 	key_mgmt=WPA-PSK
 	pairwise=CCMP TKIP
	group=CCMP TKIP
 	psk=#deleted_for_security_reasons#
}
```

And..YES, I did enable my WPA+WPA2 on my netgear (latest firmware).


Any suggestions?

g.

---

