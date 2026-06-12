---
title: "Another &quot;wi-fi is disabled by hardware switch&quot; Problem here."
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by Darth_Salva on 2015-03-26
Hi, after like 6 or 7 years i've returned to linux and choosed lubuntu this time.

I have a small toshiba nb200 netbook and i have the problem "wi-fi is disabled by hardware switch". 
command rfkill list all give this:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

-My wireless card is an atheros ar5b95, i've already installed the backports driver ath9k and tested the ath5k driver too.
-The device works fine using a live-usb distro of kali linux (... And even injects :biggrin: ), under windows it works fine too.
-I've tested using another wireless card compatible with the same driver (an atheros ar5bxb63) and works fine in lubuntu.
-There's no physical switch in the netbook to lock/unlock the wireless card.

So, i have the ar5b95 "hard blocked" only under lubuntu, and the ar5bxb63 working fine under that same distro (but i want to use the ar5b95).

Any ideas? I'm blocked :/

---

### Post by Darth_Salva on 2015-03-27
Ahh nevermind... That's one of the reasons i stopped using linux 6 years ago... Too much time solving problems just to have a working system.

I'll try with another distro...

---

### Post by kerry_s on 2015-03-27
try this, should be fine on those low specs.
[http://elementary.io/](http://elementary.io/)

---

