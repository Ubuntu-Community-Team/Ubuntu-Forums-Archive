---
title: "What Wireless Card Should I Get?"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by LaneLester on 2007-12-14
Yes, I know there's a list, but surely you can recommend one that I can count on being supported by Ubuntu without a lot of fiddling.

I have to travel to another site, and I'm really disgusted that I'm going to have to boot my notebook to Win XP in order to use wireless. My card is a Netgear 401 which has been out forever, and it's incredible that Ubuntu Gutsy doesn't support it. I've read a bunch of threads of people who have struggled with this issue. :(

Lane

---

### Post by Junglizer on 2007-12-14
> **LaneLester said:**
> My card is a Netgear 401 which has been out forever, and it's incredible that Ubuntu Gutsy doesn't support it. I've read a bunch of threads of people who have struggled with this issue. :(

Lane

Its not so much how long the card has been around its a matter of how open the manufactures of the components are. One thing that you need to be sure to note when seeking help for wireless cards is to say which actual radio/chip it has in it. This is also dependant on the version of the card. A Netgear may have been around a long time but as they release newer versions they change which wireless chip they use in the product, so version 5 may work great b/c its an Atheros chip but versions 1-4 might be a pain in the neck b/c they have Broadcom chips (Broadcom is notorious for being "difficult" to work with, though a lot of that is changing). So unless the makers of the chip release open documentation on the chip itself and working with the firmware it comes upon the developers to reverse engineer it and try to produce a driver that is sufficent. 

The only card that I can 100% recommend for compatiblity is the [Ubiquity SRC]("http://www.ubnt.com/products_src.php4"), however this is a rather expensive card (roughly $130 USD) with an Atheros AR5213, however it lacks a built in antenna and requires and external though it has dual mmcx ports. Long story shot this card is bada**, but it would be a waste of power, battery-life and money to use this just to surf out to facebook.

---

### Post by LaneLester on 2007-12-14
> **Junglizer said:**
> Its not so much how long the card has been around its a matter of how open the manufactures of the components are. One thing that you need to be sure to note when seeking help for wireless cards is to say which actual radio/chip it has in it.

I see. All I can add is that it's "Rev. D." I don't know about the chip; is that something Linux can tell me?

> The only card that I can 100% recommend for compatiblity is the [Ubiquity SRC]("http://www.ubnt.com/products_src.php4"), however this is a rather expensive card (roughly $130 USD) with an Atheros AR5213, however it lacks a built in antenna and requires and external though it has dual mmcx ports. Long story shot this card is bada**, but it would be a waste of power, battery-life and money to use this just to surf out to facebook.
Yes, well, thank you. I hope there will be another recommendation that is a bit more affordable. :)

Lane

---

### Post by miesnerd on 2007-12-14
I cant promise you anything, but I have a "friend" who bought a Hawking wireless dish to "borrow" their neighbor's internet. It worked flawlessly with 7.04 and 7.10. I read somewhere that as a disclaimer, they dont support linux. But Ive seen on opendrivers.com that they have a linux download (as a .zip). I wish my laptop had a hawking instead of broadcom, which I would reccomend to avoid like the plague. That company snubs its nose at linux. My, uh, friend that borrows internet gets great signal, and great range from his neighbor and good speeds (for free!). I happen to know that the dish they make can connect to networks over 200 yards away, in an apartment complex.

---

### Post by miesnerd on 2007-12-14
: [http://www.hawkingtech.com/products/index.php?CatID=19&amp;FamID=33](http://www.hawkingtech.com/products/index.php?CatID=19&amp;FamID=33) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				forgot to link you.

---

### Post by woodcarver on 2007-12-14
I have Gutsy and recently got the Dlink DWL-G650 plugged it and logged in, no issues!
It was about 40USD from Tiger Direct. :)

---

### Post by LaneLester on 2007-12-14
> **woodcarver said:**
> I have Gutsy and recently got the Dlink DWL-G650 plugged it and logged in, no issues!
It was about 40USD from Tiger Direct. :)

Thanks to everyone who responded. I think I'll go with this one. It's $28.43 at Amazon,com, and one of the reviewers also recommended it for Linux.

**[COLOR="Red"]Later: [/COLOR]**The DWL-G650 arrived, and to be sure all was well, I first installed it in Windows. And of course, it was simple with no hitches. Then I booted Xubuntu Gutsy. No Internet. So I opened the Network interface, disabled roaming mode, and the router's ESSID was detected. I set the IP to DHCP, and left everything else alone. No joy.

I do not use password security on my home LAN, preferring to use a MAC filter list to keep outsiders out. Is the fact that I have no password to give the Network interface a problem?

Or do you have some other suggestion about how I can get wireless working? I'm going to be using this laptop at a college, and I'm hoping to have Xubuntu for onlookers to see, rather than Windows XP. Please help me achieve this!

Lane

---

### Post by LaneLester on 2007-12-17
Well, I think I've succeeded. I found the [Wireless Trouble Shooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-2e426b202454e898950d58705107ed41c99dc25b"), and following its suggestions:

confirmed detection of card and assignment of driver
added pci=noacpi to the boot options: no good
sudo dhclient ath0: nope, not yet
sudo invoke-rc.d networking restart: and that did the trick!

A reboot confirmed that I still had wireless service.

I wonder if I had done the above with the old card... oh, well. :)

Lane

---

