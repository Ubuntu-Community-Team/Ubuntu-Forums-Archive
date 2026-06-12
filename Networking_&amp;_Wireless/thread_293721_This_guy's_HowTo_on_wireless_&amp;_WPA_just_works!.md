---
title: "This guy's HowTo on wireless &amp; WPA just works!"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by ArgentSilver on 2006-11-05
I have been fighting awhile now to get wireless with WPA working under Dapper. Finally decided to get a card that seems to have native support so I don't have to use ndiswrapper. So after some research I found the Dynex DX-WGDTC 802.11b/g at Best Buy for $35 (ie. cheap!). It presently uses the Atheros chipset, which works well with Dapper.

Then this info worked flawlessly and easily to get it running with WPA.

[http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)

Had me up and running in about 15 minutes, after I had spent hours over the last month trying to get WPA to work. :mrgreen:

---

### Post by DC@DR on 2006-11-05
It looks really simple, huh? I had to edit /etc/wpa_supplicant.conf, then edit /etc/network/interfaces to load wpa_supplicant.conf while boot up, etc...This guide is really easy, I would try it next time when I install Ubuntu for one of my friend to see how it works :p...Thanks for the link :)

---

### Post by ArgentSilver on 2006-11-05
I had to share that procedure...That guy is a guru as far as I'm concerned! (Bows and chants "We're not worthy!")

I originally ran afoul of what I have since discovered is a common experience, namely; I ordered a wireless card that the online sources said was a certain chipset and good under Linux, only to find that the manufacturer had changed the chipset and not the model #. But I didn't really pay enough to make it worth paying to ship the card back for a refund. So then I spent a bunch of time getting it to work with ndiswrapper. Then I moved on to try for WPA, which never worked.

I was completely gobsmacked at how easy it was with a new card and that procedure... :D

---

### Post by hairypete on 2006-11-07
This guide looks quite promising, although I have been having problems so far with network manager in that when I install it, clear down all but the first two lines in /etc/network/interfaces and reboot with my ralink 2400 pcmcia card in the slot, the power light on the card comes on, but when I click on network manager, all i get is a message saying that "no network devices have been found"  Any ideas?

---

### Post by hairypete on 2006-11-10
bump

---

### Post by wieman01 on 2006-11-10
Mmm... I have dropped NetworkManager for a number of reasons, but mainly for its lack of support for Static IP. If you guys don't mind getting your hands a bit dirty, you can try this: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

---

### Post by ArgentSilver on 2006-11-10
> **wieman01 said:**
> Mmm... I have dropped NetworkManager for a number of reasons, but mainly for its lack of support for Static IP. If you guys don't mind getting your hands a bit dirty, you can try this: [http://www.ubuntuforums.org/showthread.php?t=202834]("http://www.ubuntuforums.org/showthread.php?t=202834")

Also, response #3 to the guide that I linked in the original post has some howto info for Static IP. Can't vouch for how well it might work.

---

