---
title: "can't get either of two wireless cards to detect a network"
date: 2007-11-17
forum: Networking &amp; Wireless
---

### Post by jcankrom on 2007-11-17
i already posted this at forums.debian.net, but ubuntuforums.org has much more activity, and ubuntu is based on debian, so...
my wireless worked fine in XP, fine when I switched to Ubuntu Feisty, fine when I switched to Debian Lenny, based on DVDs from desktoplinuxdvd.com burnt in June, 2007. but when i did a massive upgraded from the june version to the present, poof, no more wireless.
for the record, I have an HP Pavilion ze4300us laptop, these wireless cards are pcmcia cards.

wireless card #1: Zonet 1502 (Marvell Libertas): feisty, and the june version of Lenny (2.6.18 kernel) required the use of ndiswrapper. when i upgraded to 2.6.22-2-k7, the lights were out on this card. so the first thing i checked was whether ndiswrapper was installed. sure enough, i had to recompile the driver. once that was done, the wlan0 interface appeared, and the lights went on on the card, but rather than a constant power light and a flashing activity light, i had a flashing power light. so, thinking maybe ndiswrapper wasn't working right, i uninstalled it, reinstalled it, recompiled it, recompiled it with the 1.49 source, etc. nothing worked. then, i did my homework and realized that the 2.6.22-2 kernel comes with a libertas driver builtin. i uninstalled ndiswrapper and restarted, but still saw no lights on the card and no interface. so back to ndiswrapper, i tried blacklisting the libertas driver, and even recompiling the kernel without the libertas driver. all to no avail. so the result is with the libertas card and ndiswrapper, i have a flashing power light, a wlan0 interface, but i cannot detect any networks. i'm pretty sure the flashing power light is an error signal, though its not listed in the card's documentation. the power light is constant on when the card first gets initialized, but when the card scans for a network, the activity light flashes for a second, then stops and the power light starts flashing. very annoying.

wireless card #2: Cisco Aironet 350 using airo_cs, airo driver. similar problem, i have a flashing power/status light and a flashing activity light. this card gives a wifi0 interface and an eth2 interface. again, i see no networks listed. i've never had great luck with this card, despite its good reputation. but i should be able to detect a network.

i've tried network manager
i've tried wicd
i've tried iwlist wlan0 scan
nothing lists any networks, and i'm pretty sure the flashing power/status light is an error in initializing the card. i'm not an expert with wireless or with lenny. but i have an idea what to expect from my cards, and i've checked the forums on these issues as best as i can

i appreciate any suggestions, because i'm at a total loss of what to do next. i just bought a house directly across the street from a public library and really want to mooch off their free wireless internet. i have confirmed they have an open network -- no security features 
please don't flame me for seeking help with a debian system on ubuntuforums. 
thanks!

---

### Post by jcankrom on 2007-11-19
-=bump=-

come on, some one has to have some suggestions...
please? :(

---

