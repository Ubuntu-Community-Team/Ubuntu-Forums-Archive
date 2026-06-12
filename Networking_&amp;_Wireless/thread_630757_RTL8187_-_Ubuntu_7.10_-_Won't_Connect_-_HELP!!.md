---
title: "RTL8187 - Ubuntu 7.10 - Won't Connect - HELP!!"
date: 2007-12-03
forum: Networking &amp; Wireless
---

### Post by andrew.pope on 2007-12-03
I am currently trying to access my wireless network on Ubuntu server 7.10. The drivers were automatically installed as when i type iwconfig it lists wlan0 but it is not connected as signal strength and link quality are 0. When i type sudo iwlist wlan0 scanning it says 

wlan0.         Interface doesn't support scanning : network is down

Any suggestions on what i could do?

If you need more info just ask

And im a linux newbie so please make it understandable!

Thanks in advance,

Andy

---

### Post by syxbit on 2007-12-20
i just bought an Asus p5k-e/wifi with the RTL8187 onboard wireless for my new desktop
was having constant disconnect issues.
i installed hardy, and it was better. Today i got the 2.6.24 kernel update, and it's been perfect since then.
2.6.23 and above have the mac80211 stuff in them, that includes more wireless drivers natively.
it may not be ideal to use hardy for you, as it's alpha.
but maybe you could just grab the hardy kernel, and install it in gutsy

---

