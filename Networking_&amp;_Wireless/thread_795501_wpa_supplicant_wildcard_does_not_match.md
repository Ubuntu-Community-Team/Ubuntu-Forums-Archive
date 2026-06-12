---
title: "wpa_supplicant: wildcard does not match"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by Zibri on 2008-05-15
In my wpa_supplicant.conf i have the following network block:

network={
	key_mgmt=NONE
}

This should, according to various howtos/example wpa_supplicant.confs and following excerpt from the wpa_supplicant changelog be matching any non WPA ssid, since the ssid value is omitted.

[quote=wpa_supplicant changelog]
added support for 'any' SSID wildcard; if ssid is not configured or
is set to an empty string, any SSID will be accepted for non-WPA AP[/quote]

However, wpa_supplicant is ignoring open APs because of "SSID Mismatch". I can connect to the same AP if i add the ssid as a new network block with key_mgmt=NONE.

I use iwl4965.

---

