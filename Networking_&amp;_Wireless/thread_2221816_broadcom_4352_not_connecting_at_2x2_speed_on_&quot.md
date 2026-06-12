---
title: "broadcom 4352 not connecting at 2x2 speed on &quot;N&quot; network"
date: 2014-05-03
forum: Networking &amp; Wireless
---

### Post by keratos2 on 2014-05-03
Ubuntu Saucy laptop with broadcom BCM4532 and AC56U dual band 2 stream router , using 802.11n network..


Using hardware drivers app, I installed proprietary broadcom driver "wl" v6.30.223.141

I can only connect at max  150mpbs on 2.4GHZ , like a stream is missing. I should be able to connect at 300mbps (granted throughput will be much lower, but link speed should be 300mbps). On the laptop, How can  I check how many streams I'm using?

Ive heared I need to connect using WPA2/AES but I note on my laptop (used dmesg|grep 80211) that  kernel module 80211_crypt_tkip is used but not 80211_crypt_ccmp. How can  I check this? Ive searched /lib/modules (find /lib/modules -name  "80211" -print) for a 80211_crypt_ccmp , but nothing.

Also, where do I get firmware for my 80211 so that I can set regulatory domains to GB (defaulting to 00 at moment and "iw reg set GB" prints an error)

---

