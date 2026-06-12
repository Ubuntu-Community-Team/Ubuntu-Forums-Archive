---
title: "ath0 stopped working after suspend"
date: 2006-07-25
forum: Networking &amp; Wireless
---

### Post by eClaW on 2006-07-25
Hey guys!

My Netgear WG511T worked alright today but then after suspending, it stopped working at all. Dapper doens't seem to be able to find it anymore. Suspending worked totally perfect before (needed some tweaking tho)!

A few hours ago (when it still worked) I changed some settings regarding wireless profiles, then I tried to install NetworkManager which came up with an error during ./configure. Don't know if any of this caused the problem, since downloading worked until the second I closed the laptop's lid.

dmesg | less comes up with
```
ath_hal module license 'Proprietary' tains kernel
```

So... what can I do? ](*,)

This seems very strange to me because the card worked out of the box and I did not have to configure it at all and now suddenly it's gone?! :confused:

Hope someone can help

---

### Post by eClaW on 2006-07-25
Well, I kind of solved the problem by inserting the card into the other PCMCIA slot. So I guess the slot the card was previously plugged in is now broken? I wonder what the reason is...

---

