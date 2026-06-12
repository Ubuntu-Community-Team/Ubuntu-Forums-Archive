---
title: "wierd behaviour in wpa_supplicant / ndiswrapper"
date: 2006-12-25
forum: Networking &amp; Wireless
---

### Post by frank05 on 2006-12-25
After upgrading to edgy i found my wireless connection to be dead (oh joy!). So once again I dived into the wierd world of wireless set up on linux. I made the following startling discovery which I thought I should share with you:

Basically if you're taring your hair out trying to get wpa_supplicant working with an ndiswrapper driver you could try using "wext" as the driver parameter instead of "ndiswrapper". So you would start wpa_supplicant with:

wpa_supplicant -iwlan0 -c[your config file]  -Dwext 

instead of

wpa_supplicant -iwlan0 -c[your config file] -Dndiswrapper

Perhaps ndiswrapper is now treated as a linux wireless extension rather than something different now. If so, I haven't seen any documentation that reflects this!

---

### Post by c.dric on 2006-12-25
i was taring my hair out to get my ipw2100 running properly with wpa_supplicant (without ndiswrapper) and the ipw driver ... 

then i replaced ipw with wext and it's been working fine from then on...

---

