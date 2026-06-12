---
title: "wireless network(Intel pro 3495abg) not workin"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by A.A. on 2007-10-18
Hi,
this is my last try of using linux, this is I think the 3rd distro that lets me down what comes on the wifi. I 'v got a Intel Pro 3495ABG. On vista it runs smoothly without any problem. But on linux(including Ubuntu, I tried it two minutes ago on 7.10). It asks for my WEP encryption, I entered it(the exact way it shows on vista, shared key and WEP 64/128 Hex, after two minutes without making a connection it again asks me for an encryption, so I tried without encryption and I disabled it in windows via my router. In ubuntu, still no luck...Help please, if I can't get it fixed, I will definatly stop using linux. I like linux, but if I don't have internet on it..I 'm lost!
thanks!

EDIT: I did search on the forum, In a topic a guy was talking about upgrading his BIOS, I did, no results...

---

### Post by Hero of Time on 2007-10-18
Did you try the sticky HOWTO on top of this forum? It should work just fine, with the network manager or via wpa_supplicant. If you go the wpa_supplicant way, be sure to create a conf file for it and point to it. When using WEP with wpa_supplicant, you only need the ssid, scan_ssid, key_mgmt, web_key0 and wep_tx_keyidx sections.

---

