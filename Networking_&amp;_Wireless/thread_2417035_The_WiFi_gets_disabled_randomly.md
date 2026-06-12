---
title: "The WiFi gets disabled randomly"
date: 2019-04-19
forum: Networking &amp; Wireless
---

### Post by elcotu on 2019-04-19
Hi folks,
This is my first post. I m having a trouble with a Lenovo Ideapad S 120, it's a small notebook. I installed Lubuntu a couple months ago, with excellents results.

Two weeks from now, the wifi device doesn't get recognized every time I boot. I mean, sometimes it gets recognized and work excellent, and other times it doesn't get recognized. By now I don't have any clue in what could be the problem, but I do note that when the 
wlp2s0 is not recognized, the command sudo service network-manager status retrieves, among others, a line stating that cannot read state file /run/network/ifstate

This is the result of the networking script, but I ran it now with WiFi recognized properly:

[http://paste.ubuntu.com/p/mfpQ8j3twq/](http://paste.ubuntu.com/p/mfpQ8j3twq/)

When the card doesn't get recognized, I see this error when I query dmesg | grep ath:

ath10k_pci failed to wake target

Could this be something physical? I move the laptop a lot, that's why I bought this small one.

Saludos,

P.S.: I'm not a native english speaker so if something is badly expressed please tell me and I'll rewrite it

---

### Post by praseodym on 2019-04-20
Change the channel to the fixed "1" in your router

---

### Post by elcotu on 2019-04-20
Hi praseodym, I'll give it a try.
Meanwhile, I bought an USB - WiFi adapter and WiFi seems to work fine with it.

---

