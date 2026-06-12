---
title: "wpa_supplicant"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by avelala on 2007-01-30
I am having a heck of a time trying to connect to the secure network that we have at our university, i am new to Ubuntu, but have run Red Hat 9.0 a couple years ago.  These are the specs of our network

```

network={
        ssid="HIDDENSSID"
        proto=RSN
        key_mgmt=WPA-EAP
        pairwise=CCMP
        eap=PEAP
        identity="domain\username"
        password="********"
}

```

I have installed network manager to some prevail, but it only works when the signal is broadcasted, and it works very inconsistantly.  I have heard many things about wpa_supplicant 0.5.7, but i have v0.5.4 and i don't know how to compile to upgrade, much less run that program for it to work.  

It would be cool if somebody could help me with this, I ran through weisman1's tutorial, but that just got me confused...   and it actually caused me to somehow disable the wireless part of Network Manager, so now i can't connect to any wireless which doesn't help me at all.  

any help is greatly appreciated
Adam.

---

