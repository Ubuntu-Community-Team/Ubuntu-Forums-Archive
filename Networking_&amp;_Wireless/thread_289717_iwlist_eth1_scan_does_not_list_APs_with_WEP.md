---
title: "iwlist eth1 scan does not list APs with WEP"
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by RikoW on 2006-10-31
Hi all,

I have a intel contrino with the intel wireless pro 2100 in a DELL D600. In principle wireless networking works flawlessly.

However, when I do an *iwlist eth1 scan* at work, I only find the APs which don't have a WEP encryption. The intranet wireless access which is encrypted using a WEP key I don't see. However, I can connect to it knowing the ESSID and the WEP key.

I assume, that *iwlist eth1 scan* should show me all APs so also the ones with only WEP encrypted access, right?
I also assume, and that is the real reason for this question, not being able to find the WEP AP with iwlist is the reason, why NetworkManager will not show it as available network. I can connect to it, if I configure the encrypted connection each time again, but that is not really helpful.

Thanks for any reply!

          - Riko

---

### Post by Nobber on 2006-10-31
Um, dunno if this is relevant, but do the APs with WEP broadcast their ESSID?

---

### Post by RikoW on 2006-10-31
> **Nobber said:**
> Um, dunno if this is relevant, but do the APs with WEP broadcast their ESSID?

According to our admin: yes!

---

### Post by alphacrux on 2008-03-18
Looking at the date of your post you have probably resolved this or lost interest but if not or if others are interested i believe I may have an answer to your problem.

If you know the essid try setting it on the device before doing a scan (substitute your own network):
```
iwconfig wlan0 essid NETWORK
```

if this doesnt work try to read up on the different configurations of iwconfig:
```
man iwconfig
```

You might also try setting enc to open or restricted or setting a fake key based on the wep encryption (10 digit hexadecimal for 64-bit encryption aka wep40, and a 26 digit hexadecimal for 128-bit encryption wep104). Here is an example that does both of these options although I would try them one at a time and do a scan after each one:
```
iwconfig wlan0 enc restricted key 12345678901234567890123456
```

also substitue your wireless device in if it is not wlan, such as eth1, or ath0.

---

