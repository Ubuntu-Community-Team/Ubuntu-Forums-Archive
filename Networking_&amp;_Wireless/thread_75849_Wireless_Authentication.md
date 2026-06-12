---
title: "Wireless Authentication"
date: 2005-10-14
forum: Networking &amp; Wireless
---

### Post by Beanz on 2005-10-14
I have my computer at school, and I installed the wireless drivers using ndiswrapper, but the school system uses Odyssey Client authentication. ([http://www.funk.com/](http://www.funk.com/)) The authentication is the school domain user/password (windows systems) and I would like to use Ubuntu with the school internet. Does anyone know of any ways I could connect to the wireless without getting my own access point with normal WEP or WPA authentication (I doubt that they would like it).

---

### Post by lcg on 2005-10-14
[QUOTE=Beanz]I have my computer at school, and I installed the wireless drivers using ndiswrapper, but the school system uses Odyssey Client authentication. ([http://www.funk.com/](http://www.funk.com/)) The authentication is the school domain user/password (windows systems) and I would like to use Ubuntu with the school internet. Does anyone know of any ways I could connect to the wireless without getting my own access point with normal WEP or WPA authentication (I doubt that they would like it).[/QUOTE]
According to Funk's website, Odyssey Client is an 802.1x authentication client. Have a look at wpa_supplicant ([here]("http://hostap.epitest.fi/wpa_supplicant/")), which also provides a lot of 802.1X authentication mechanisms. Having used mostly WPA-PSK myself, I'm no expert here but maybe one of the supported mechanisms works for you.

HTH,
Lars

---

### Post by peterbrowne on 2006-02-26
at my school, our wifi network GGWIREless was replaced with PDSBUser on Friday - requiring Odyssey to use EAP-TTLS or LEAP. Through extensive googling, I found open1x - which is in the Ubuntu repositories. Trying it on my friends Gentoo notebook on monday - while my Acer notebook (Ubuntu) needs a new power cord

---

