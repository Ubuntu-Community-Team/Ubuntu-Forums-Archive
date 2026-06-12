---
title: "Wireless drivers for Marvell Chipset?"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by Hacker3141 on 2008-11-05
Hello,
I have been trying to get my wireless card working in Ubuntu for quite a while now. I just downloaded and installed 8.10 yesterday and since have not been successful. My card is a Rosewill RNX-G300E, and has a Marvell 88w8335 Libertas chipset. I am running Ubuntu 8.10 x64, all help is appreciated. If I am not able to find a driver, please refer me to a suitable wireless card that is most likely to work without much work. Thank you.

---

### Post by Ushi on 2008-12-21
I know this is an old post, but it's pretty high on Google for "rnx-g300e drivers linux" so I thought I'd weigh in.

I have this card and was able to make it work with ndiswrapper and the mrv8335 Windows drivers I've attached to this post. The drivers that came with the card appeared to work, but after loading the ndiswrapper module, I couldn't set the ESSID on the card (although it was able to scan using iwlist).

As root:

```
ndiswrapper -i mrv8335.inf
modprobe ndiswrapper
iwconfig wlan1
```

---

### Post by bimmer jake on 2008-12-22
this driver worked great for me.  I don't have the same wireless card but my card does use the same chip set.

---

