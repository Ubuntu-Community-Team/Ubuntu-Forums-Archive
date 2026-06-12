---
title: "NetworkManager 0.6.5 802.1x EAP/TTLS PAP"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by MaximusTG on 2007-05-08
My university has a wireless network that uses 802.1x authentication using EAP/TTLS and PAP as phase2 authentication. I had to manually configure wpa-supplicant, because NetworkManager didn't support that. Recently I read that version 0.6.5 did support this, so I built it from source, but it  seems it still isn't possible. Anyone had similar experiences?
I installed NetworkManager and nm-applet with checkinstall, so I'll attach the .deb's to this post.

---

### Post by newpants2003 on 2007-10-16
uofm ?

---

### Post by Everywhere_at_Once on 2008-01-29
lol Yeah im at the UofM, and im trying to get the secure wireless up and running.

PM me if you have any suggestions as to what works.

thanks

---

### Post by jordanius on 2008-02-08
Thanks so much for this, I spent many hours trawling through the forums but this finally fixed my problems. Cheers!

---

### Post by newpants2003 on 2008-02-17
> **Everywhere_at_Once said:**
> lol Yeah im at the UofM, and im trying to get the secure wireless up and running.

PM me if you have any suggestions as to what works.

thanks

you could try remove networking manager, using wpa_suppliant connect manually.
my friend had his ipw2200 pro working .

i could not config the networking manager connect to the uofm-auth with iwl4965 driver.

but i could connect using NDISwrapper with windows xp driver.
this is the most easy way.

but my lenovo t61p become quite unstable after i switched to windows driver, not sure why.

---

