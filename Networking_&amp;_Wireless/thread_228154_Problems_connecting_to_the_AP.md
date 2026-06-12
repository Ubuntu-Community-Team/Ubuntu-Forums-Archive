---
title: "Problems connecting to the AP"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by fluchtpunkt on 2006-08-02
Hey there!

So I have finally got Kubuntu (Dapper Drake) to work on my Acer 1522 and even (thanks to the great guides here) got the built-in wireless LAN to work.

However, I cannot connect to my router (d-link 624+). I can see the router in the wireless assistant, but every connection attempt fails.

I have tried Open System WEP, Shared Key WEP, both with ASCII and hexadecimal keys, I even tried opening the wlan completely by disabling WEP altogether, but I that didn't work either.

After each connection attempt, a line like this one is added to the dmesg output:

ndiswrapper (iw_set_freq:375): setting configuration failed (C0010015)

Does anyone have suggestions for me?

---

### Post by fluchtpunkt on 2006-08-03
OK, don't bother, it works now. This seems to be either a router problem or my stupidity, because WEP doesn't work in Windows XP as well.

I'm using WPA now (with wpa_supplicant) without problems.

I just wanted to say that this forum has been an incredible help in installing Kubuntu on both my computers now! :D

---

