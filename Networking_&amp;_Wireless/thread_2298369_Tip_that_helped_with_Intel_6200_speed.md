---
title: "Tip that helped with Intel 6200 speed"
date: 2015-10-10
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2015-10-10
Why? I have no idea. This is not a support request but rather something to try for those having wifi speed issues so move as appropriate.

Background: Router is a Linksys E2500 v3 running current NV60 mega build DD-WRT . WPA2 w/AES only encryption, 2.4 Ghz band, 5 Ghz not supported. I have one notebook - Thinkpad T410 w/ Intel 6200 wifi that was a problem child. For whatever reason I could not get connection speeds greater than 26 mb./sec. I took the machine to public wifi access points and it'd connect at around 78 mb./sec. I tried my old standby Trendnet TEW-649UB and it connected at 140 mb./sec. At this point it appeared that:

1) This machine was capable of higher connect speeds if not using the Intel 6200 adapter.

2) This machine using the Intel 6200 adapter would connect at higher speeds to other wifi access points.

3) Other machines not using the Intel 6200 would connect to the Linksys router at acceptable speeds, 70 mb./sec.+.

Well, crap. I blacklisted the Intel 6200, installed the patched RTL8192cu driver, plugged in an Edimax EW-7811Un adapter and carried on. The SSID I was using was something like Jack&Jill and the passphrase a short sentence mangled enough to not likely be found in any dictionary. I decided to change the SSID and passphrase. The SSID is 10 random characters and the passphrase is 25 or so random characters. The T410 using the Intel 6200 adapter that wouldn't connect at speeds greater than 26 mb./sec. is now connecting at 78 mb./sec. Still not 140+ mb./sec. max but usable for my purposes. I made no other changes to the router or Intel config files, just changed the SSID and passphrase. I have no clue why it worked but it did. Just something to try when all else has failed (and you can change the SSID/encryption).

edit:  O.S. is Ubuntu-Mate 15.10

---

### Post by michael337 on 2016-01-21
umm... first of all, run > iwlist wlp3s0 freq
if you see 5.XX anywhere in the terminal, you support 5ghz :D
second, my bitrate is just as decent as one of my other computers

I use a thinkpad t410 too

---

