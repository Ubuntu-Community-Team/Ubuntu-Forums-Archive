---
title: "WPA &amp; ipw2200 (Intel PRO/Wireless 2200)"
date: 2006-11-19
forum: Networking &amp; Wireless
---

### Post by karmapolice on 2006-11-19
First time trying out Ubuntu, and actually first time attempting using any linux distro in any serious way.

After installing edgy, wireless worked right away for unsecured networks. However secured networks were not visible. I spent a few hours reading posts in this form and have been banging my head against a table trying to get things working, but so far no luck. I have been able to get the wpa_supplicant running to some extent so that the secured networks are at least visible (i can see the list of them when i click Scan Networks in an app), but so far haven't been able to connect to mine using WPA.

Before I give any more details and waste peoples' times with specifics, are there any step-by-step guides getting WPA working for an ipw2200 card (Intel PRO/Wireless 2200)? Does anyone out there actually have this working with edgy?

Thank you very much!

---

### Post by wieman01 on 2006-11-19
I have a IPW2200 as well & it works perfectly with WPA1 as well as WPA2. There is a guide:

[http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

There are a number of sample scripts that you can use depending on what setup you require (WPA1, WPA2, hidden ESSID). You'll see what I mean but your "wpa-driver" is "wext" and wireless interface most likely "eth1".

Post away if you need a hand.

---

### Post by karmapolice on 2006-11-19
Awesome, that did the trick! Had to try a few combinations, but eventually got it to work using that page. :D

I'm still confused why other guides suggested using the wpa_supplicant config, but this one suggested doing it in the interfaces file...

Thanks!

---

### Post by wieman01 on 2006-11-19
Hello, 

Glad to hear it. Would you mind sharing your configuration with us? I'll possibly post it on the site for IPW2200 users... Thanks.

---

### Post by karmapolice on 2006-11-20
But of course! In the end it wasn't a very complicated configuration that was needed. I edited /etc/network/interfaces with the following contents:

> auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth1
iface eth1 inet dhcp
wpa-driver wext
wpa-conf managed
wpa-ssid linknix
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk MY_GENERATED_PSK_THINGIE

As you can see I'm using WPA TKIP which is the default choice for the "Pre-Shared Key" security mode on my Linksys WRT54GS.

Let me know if you think any other info would be useful.

---

### Post by wieman01 on 2006-11-20
Thanks a lot... No, I guess that will be fine in fact. I'll make a copy of this & post it in my thread. Have fun!

---

