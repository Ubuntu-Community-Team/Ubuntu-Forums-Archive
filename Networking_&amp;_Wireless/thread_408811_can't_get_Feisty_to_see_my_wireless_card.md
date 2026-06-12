---
title: "can't get Feisty to see my wireless card"
date: 2007-04-13
forum: Networking &amp; Wireless
---

### Post by Bdidi on 2007-04-13
I'm new to Ubuntu, and wireless is the one thing that's not going well. I've put Kubuntu 7.04-beta on my slightly aged Dell Dimension 2100; it has a Netcomm NP642 Super-G wireless PCI card installed, but no ethernet card.
When I first installed Kubuntu, I tried to activate the networking through System Settings, but got error messages saying "no such device", which made sense for ethx, but the same thing for ath0 and wlan0. :( 
So I installed ndiswrapper and followed the instructions from help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper and was able to identify my wireless card, and installed the drivers from the CD that came with the card, but wlan0 does not find the card. If I go into Terminal and try
```
ifconfig -a
```
I find that only the local loopback is listed. On the other hand,
```
cat /etc/iftab
```
returns
```
ath0 mac 00:40:f4:f6:0f:ab arp 1
```
and
```
ifdown wlan0
```
tells me that wlan0 is not configured.

Can someone tell me what I can try from here?

TIA,

Brett

---

### Post by jimrz on 2007-04-13
> **Bdidi said:**
> I'm new to Ubuntu, and wireless is the one thing that's not going well. I've put Kubuntu 7.04-beta on my slightly aged Dell Dimension 2100; it has a Netcomm NP642 Super-G wireless PCI card installed, but no ethernet card.
When I first installed Kubuntu, I tried to activate the networking through System Settings, but got error messages saying "no such device", which made sense for ethx, but the same thing for ath0 and wlan0. :( 
So I installed ndiswrapper and followed the instructions from help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper and was able to identify my wireless card, and installed the drivers from the CD that came with the card, but wlan0 does not find the card. If I go into Terminal and try
```
ifconfig -a
```
I find that only the local loopback is listed. On the other hand,
```
cat /etc/iftab
```
returns
```
ath0 mac 00:40:f4:f6:0f:ab arp 1
```
and
```
ifdown wlan0
```
tells me that wlan0 is not configured.

Can someone tell me what I can try from here?

TIA,

Brett

   you might be better off to download v 6.10 edgy eft rather than the 7.04 beta.   i understand that currently the release candidate for 7.04 is delayed due, in large part, to problems with network manager. this may be at the root of the issue you are having. or you could wait for the official release of 7.04 which is scheduled for 4/19/07 (though this could be subject to delay, as well) which should have these problems corrected. 

   personally, since you are new to linux, i would suggest that you go with the more stable 6.10 and get a bit more familiarity with your new os before messing with beta version

---

### Post by Bdidi on 2007-04-14
> you might be better off to download v 6.10 edgy eft rather than the 7.04 beta. i understand that currently the release candidate for 7.04 is delayed due, in large part, to problems with network manager. this may be at the root of the issue you are having. or you could wait for the official release of 7.04 which is scheduled for 4/19/07 (though this could be subject to delay, as well) which should have these problems corrected.

Urk! Not the most encouraging news - I'd really like to get this resolved soon.

I had previously tried v6.10 of xubuntu on this machine and ran into problems with the USB wireless connector not being recognised at all - scanning through this forum, I came across posts where Feisty was suggested over Edgy supposedly because of better handling of wireless. Kubuntu 7.04 wouldn't recognise the USB connector either, but I've now acquired the PCI card, and at least that shows up.

Unless a better suggestion comes along, I suppose I'll try putting 6.10 back on and seeing if that gets me any further.

Thanks for replying, jimrz.

---

