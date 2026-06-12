---
title: "What's the best wireless card for Ubuntu 7.04"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by Lylepalooza on 2007-05-18
Hi there,
I would like to know what people in this community think is THE best, easiest to install wireless card out there.
I don't care if it is PCI, PCMCIA or USB, I just want to know which one is likely to work almost out of the box.

I have personally tried a Belkin F5D700 v3000 and a Netgear WG311v2, both of which seem to be two of the most buggy cards under the 7.04 release, and that is after trying everything.

I heard Intel was really good, but not sure what cards they make (and Google isn't showing any love).
Any ideas?

---

### Post by gradedcheese on 2007-05-18
I have a writeup [over here]("http://andrey.thedotcommune.com/wireless.html") with some suggestions.  Executive summary: Atheros and Ralink, or Intel (though that's more of an onboard MiniPCI thing unfortunately).  Stay away from USB dongles, Broadcom, and Marvell chipsets.  However note that the card itself (Belkin, etc) doesn't mean much, you need to know its chipset ahead of time or buy from a store with a good return policy ;)

---

### Post by Lylepalooza on 2007-05-18
Hrmm, I might see if I can find one with an atheros chipset then, as I haven't had much luck with a ralink shipset on the Belkin. Other than that, I might just hang out for the next release of Ubuntu and see if any headway has been made with wifi. I wonder if there is any Ubuntu OS that works better with wireless than another. I know a lot of people seem to be having trouble with Network Manager this time around (7.05) though they didn't with earlier models.

---

### Post by aysiu on 2007-05-18
Intel Pro Wireless 2200 works great for me.

---

### Post by gradedcheese on 2007-05-18
Well, you can read my explanation (link in original post) and see what the problem is (and no, waiting for a newer version of Ubuntu won't fix anything).  The situation will improve, but only when the chipset makers start providing documentation.  Things like NetworkManager are just user-space layers on top of the drivers, the drivers are really the issue.  There's a reason why Intel's chips are supported and Broadcom's are not (except for one, which was reverse-engineered).

---

### Post by stchman on 2007-05-18
> **Lylepalooza said:**
> Hi there,
I would like to know what people in this community think is THE best, easiest to install wireless card out there.
I don't care if it is PCI, PCMCIA or USB, I just want to know which one is likely to work almost out of the box.

I have personally tried a Belkin F5D700 v3000 and a Netgear WG311v2, both of which seem to be two of the most buggy cards under the 7.04 release, and that is after trying everything.

I heard Intel was really good, but not sure what cards they make (and Google isn't showing any love).
Any ideas?

Both Atheros and Intel wireless work out of the box with Feisty.

---

### Post by cryogenic on 2007-05-18
Just make sure if you get an atheros based card that it's not draft-n... go to [www.madwifi.org](www.madwifi.org) and look up the list of compatible cards. Atheros hasn't released their new HAL to the open source guys yet so their support for the newest cards is pretty limited (if not nonexistent in many cases). Intel cards all work, to my knowledge. If you have an open miniPCI slot, go on ebay and look for a 3945 (which is a/b/g) or a 2200. Both work right out of the box with no setup required. Just make sure networkmanager is installed.

---

### Post by spd106 on 2007-05-18
The Free Software Foundation have a list of cards support natively in Linux that don't require binary firmware or other non-free code, [http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

---

