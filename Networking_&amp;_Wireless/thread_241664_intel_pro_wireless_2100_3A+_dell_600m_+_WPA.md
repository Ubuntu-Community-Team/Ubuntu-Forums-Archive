---
title: "intel pro wireless 2100 3A+ dell 600m + WPA"
date: 2006-08-22
forum: Networking &amp; Wireless
---

### Post by venky80 on 2006-08-22
I have a dell 600m with intel pro wireless 2100 I am trying to make  WPA work on my system. I have gone through countless HOW to's and I am still not able to make it work. Can anyone suggest me any linw which has been verified, because I ofter find some command in the how-to is almost always broken!

---

### Post by ingo on 2007-01-26
Right, a bit late and you may have got it working already, but try installing knetworkmanager. Only thing to bear in mind is that 'cos it deals with everything wpa throws at it itself, you have to uncomment any changes you made to /etc/network/interfaces and rename your wpa_supplicant.conf to something else.

Works a dream for me.

---

