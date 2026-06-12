---
title: "Using ipw2200 as wireless access point"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by accord on 2007-12-07
I have a notebook with ipw2200 wireless, and I'd like to use it as an access point. I found [this web page]("http://wiki.linuxquestions.org/wiki/Wireless_networking#Create_an_access_point"), but when I do```
accord@genesis:~$ sudo iwconfig eth1 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Invalid argument.


```

I guess that's because ipw2200 doesn't support master mode. I found [ipw2200-ap]("http://ipw2200-ap.sourceforge.net/"), but I don't understand what it's for. Also, could someone explain where [hostap]("http://hostap.epitest.fi/") fits into all this? Or does it have nothing to do with what I'm looking for?

---

### Post by DonaldPK on 2007-12-26
i'm looking to do exactly the same thing on my notebook. still researching on this.

AFAIK, hostap is just a card driver for Intersil Prism chipsets and not for intel wireless. i'm using that and hostapd with an old 3Com wireless card to run as an access point.

i think ipw2200-ap is a firmware replacement to use ipw2200 cards as an AP but I am not completely sure yet. will post further if there is success.

---

