---
title: "atheros mini pci  AR5212 chipset"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2007-09-13
Looking for a quick opinion (although my explanation is a bit detailed):
Would installing madwifi from source possibly fix this, or alternatively and maybe more easily, is there something I can tweak?

First, this card works fine in Knoppix and Win XP.

In Gutsy, it shows a connection, but I can't often connect to the internet at boot even with a few bars in the network-manager icon.  Network manager usually shows a correct IP address for my wireless setup, although more often than it should, it will also give me a junk IP which I cannot clear without a bunch of acrobatics.

I tried WICD, and it seemed a bit more stable than network-manager (KDE), but I have the same issues other than it tends to clear any junk IP that is rendered on boot so that it will reconnect more easily.

I have had the Atheros HAL driver checked and unchecked in restricted-manager and it does not seem to make a difference with this issue.

Oddly, since this card can "scale" its connection, the connection speed is all over the map.  I can be a meter or 10 meters from the router and when I do get a connection, it is very unstable and can go from 54 mbps to 1 mbps and anywhere in between within seconds/minutes and I am not moving nor is there anything between the laptop and router.  The signal strength is also fairly weak.

If I open kwifi manager, the scale might show up as a 108, 54, or 11 MBPS card, depending on the "mood."  Something is NOT stable obviously, although if it shows up as 108, or 54, it eventually shows up as 11.

Knoppix 5.1.1 handles this card with ease.  So does XP.

I actually put my broadcom card back in and am using restricted-manager (uses fw-cutter) so I can get a stable connection.

Would installing madwifi from source possibly fix this.

Edit: I have a full sized atheros card in my desktop that connects to the same router with NO issue... with Gutsy.

---

### Post by oooooops on 2007-09-13
I have an IBM T42p that has this chipset.  I went through some of the same things you are talking about (except with Feisty).

In desperation I installed madwifi from source and then things started working fine.  It really wasn't as difficult as I thought it would be and it paid off for me.

---

### Post by maestrobwh1 on 2007-09-13
Actually, I found this post... which is sort of a hybrid of installing from source.  It installs the latest debian madwifi and configures it specifically for your kernel:
[URL="http://ubuntuforums.org/showthread.php?t=485579&highlight=how+to+madwifi+source"]
http://ubuntuforums.org/showthread.php?t=485579&highlight=how+to+madwifi+source[/URL]

---

