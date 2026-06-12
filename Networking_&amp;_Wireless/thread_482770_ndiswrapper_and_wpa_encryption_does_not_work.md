---
title: "ndiswrapper and wpa encryption does not work"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by darkshadow on 2007-06-24
I am running 64bit Feisty and when I visited my mom last night I could not connect to her wpa (aes only) encrypted network using ndiswrapper. But if I rmmod'd it and inserted bcm43xx I would just start working fine. With the added bonus of network manager showing her network and all the neighbors with 2-4x signal strength.

What could be wrong since I need the extra speed of ndiswrapper since bcm43xx is limited to 11M

I have zero problems using ndiswrapper for:
Unencrypted (one of her neighbors)
WEP (my cousin)
WPA2 (AES) (mine)


I would like to figure this out since I am to lazy to flash her router with dd-wrt to enable use of wpa2

It use to work under Edgy (and Dapper) which is what I used to setup her network last time I visited.

---

### Post by darkshadow on 2007-06-24
Oops forgot to finish before posting.

Network Manager says I am at 50% signal but never recieves a ip from the router

Manually running "wpa_supplicant -Dwext -ieth1 -c/etc/wpa_supplicant/wpa_supplicant.conf"
spews out errors that are something like "eapol-key counter did not increase dropping packet" (not a exact quote)

---

