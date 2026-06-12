---
title: "Which WLAN USB to buy"
date: 2007-01-12
forum: Networking &amp; Wireless
---

### Post by ashrack on 2007-01-12
At home we have a wireless ruter. Now we would need a WLAN USB KEY for notebook. And I want to buy one that is supported buy LINUX.
Which one should I look?

ps. And I am from Europe Slovenia

---

### Post by dmizer on 2007-01-12
have a look here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

you should be able to find something listed there which is available to you locally.

---

### Post by ashrack on 2007-01-12
that link really has very poor documentaion for USB dongles.
So thus far I believe the following two are of use:
Asus WL - 167g
and
trendnet 54g

which one do U thing, or U have any better recommendations

---

### Post by dmizer on 2007-01-12
poor documentation for usb dongles because usb dongels are frankly ... not well supported.

i have a linksys that works out of the box in dapper, but i don't remember what version it is and it's loaned out.  i'm also not sure if it works in edgy or not.  i believe it's the wusb54g v4 dongle, but i'm not positive.  soon as i find out for sure, i'll post ... if you're interested.

---

### Post by Enverex on 2007-01-12
Please do, I'm interested in finding one with support for WPA2+AES support personally (don't like buying PCI stuff because of it being phased out and with USB it's easier to use on any other machine if I ever need it).

---

### Post by dmizer on 2007-01-13
i have confirmed that my usb dongle is indeed the wusb54g v4.  it has also been since breezy that i tried it in ubuntu.

and i can't guarantee my usb card to work with wpa or aes because my router is not capable of either (to the best of my knowledge, that level of encryption is only available in the states and the uk)

besides, usb isn't a real fantastic through-put for a network connectivity.  it's flaky even in windows, so i suggest using it only as a stand in rather than depending on one as your main source of wireless connectivity.  if i recall correctly, i believe i/o is slower than pcmcia too.

i ran into one of those computers with the new express pcmcia slots.  i thought that was about the most ridiculous thing to distribute a computer which relied on a technology not readily available in the consumer market yet.  especially one so heavily used as pcmcia.

linksys also now makes a flash memory wireless network adapter.  don't know much about it though.  it would seem that implementation in linux might be difficult.

---

