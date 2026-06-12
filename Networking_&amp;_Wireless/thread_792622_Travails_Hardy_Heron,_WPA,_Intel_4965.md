---
title: "Travails: Hardy Heron, WPA, Intel 4965"
date: 2008-05-13
forum: Networking &amp; Wireless
---

### Post by zoiks on 2008-05-13
Well, after much trial and error (especially error) I've discovered a couple of things about wireless networking on Hardy with the Intel 4965 a/g/n chipset while using WPA and hidden ssids.

1) By and large, connecting to an AP using WPA and a hidden essid doesn't seem to work. There must be *some* way to get it to work, but it's not obvious to me. I say there's a way because the Wicd software can do it, and it's just a python interface to the networking functions and wpa_supplicant. It's notable, however, that the Wicd program (the daemon in particular) won't auto-connect to an AP if the network's essid is hidden. When using Wicd, I had to find the network and reconnect it every time, even when "auto-connect" was chosen for the network. I wasn't exactly impressing my wife when I had to explain to her the steps to get the network going when she logs into her own user account.

2) A delay seems to be needed to get the network to connect on startup. I have no idea why. But the "pre-up sleep 10" line in my interfaces file shown below makes my connection repeatable whenever I boot up. (Before adding that line, I had to restart networking every time I booted the machine.)

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 down
	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 down
	pre-up sleep 10
	wpa-driver wext
	wpa-ssid my_ssid
	wpa-ap-scan 1
	wpa-proto WPA
	wpa-pairwise TKIP
	wpa-group TKIP
	wpa-key_mgmt WPA-PSK
	wpa-psk my_PSK

```

I might be able to change the sleep time to 5 instead of 10, I don't know. Also the ifconfig wlan0 up/down lines may or may not be doing anything - I'm too lazy to check right now. But the interfaces file shown above works great for me.

When the network ssid was hidden, I couldn't even connect when wpa-ap-scan was set to 2.

I sure wish this stuff were easier to figure out. I've spent hours and hours going through howtos and other docs trying to get this to work. At least it's now working reliably on my new laptop (HP dv6700t).

---

### Post by OoooMatron on 2008-05-18
I have problems with my laptop intel wifi with WPA. In short, it is not reliable with disconnections you cannot seem to recover from without a reboot. This morning I loaded up my laptop and had connectivity for about 10 seconds before it just died.

WPA works great with my netgear USB adapter though.

I have gone back to WEP 128, at least it works.

---

### Post by zoiks on 2008-05-20
FWIW, I've since gotten rid of these lines:

```
	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 down
	pre-up ifconfig wlan0 up
	pre-up ifconfig wlan0 down

```

and everything still works, clearly they weren't necessary. (If anything they might have prevented a proper connection or two on startup.)

Otherwise still working fine.

---

