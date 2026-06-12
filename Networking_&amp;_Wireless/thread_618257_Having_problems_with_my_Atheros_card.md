---
title: "Having problems with my Atheros card"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by Enigmatic on 2007-11-20
I have an Atheros ar5006xs. I've never had the best of luck with the card, it seems very flaky when it comes to connecting to APs. I can be trying to connect to the school's unsecured AP (with say 50% signal quality) and people with Windows can connect almost instantly while mine just sits there and then never connects. 

Generally it fails to get an IP address, but the DHCP server isn't down. Once I had an 85% signal quality, all 4 bars. On the first try it never connected, finally did on the second one. I tried connecting to a home WEP AP, and it just sat there saying "waiting for network key".

I recently did a fresh install of 7.10, but had these issues with previous versions.

Not sure if there's something I should look into software wise, or should I just buy a new card?

---

### Post by unisol on 2007-11-20
check the restricted driver manager, and see if your wireless card is there. if it is enable it.

---

### Post by rustybronco on 2007-11-20
I would try the madwifi drivers if the above post doesn't work  [http://madwifi.org/](http://madwifi.org/)
[http://madwifi.org/wiki/Compatibility](http://madwifi.org/wiki/Compatibility)
[http://madwifi.org/wiki/Compatibility/Gigabyte](http://madwifi.org/wiki/Compatibility/Gigabyte)...
"AR5414 aka AR5006XS Single Chip Solution" 
or search for ar5414.

---

### Post by Enigmatic on 2007-11-20
I don't see the wireless card listed, but I do see the Atheros Hardware Layer.

Is there an easy way to switch to the madwifi drivers within the package manager?

---

### Post by rustybronco on 2007-11-20
Haven't forgotten about you, kind of busy here at work and I may have to continue it at home.

***EDIT*** no you can't install via synaptic, you have to do the madwifi installation.

---

### Post by rustybronco on 2007-11-20
> **Enigmatic said:**
> I don't see the wireless card listed, I wouldn't worry to much about the card listed, it's the chipset that matters, and it appears your chipset is supported.

Also see kevdogs finest in my signature...

*** please don't consider me an expert by any means, just trying to help****

---

### Post by rustybronco on 2007-11-21
have you found an answer yet?

---

