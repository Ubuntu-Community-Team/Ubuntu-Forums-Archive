---
title: "Will 4Yr old ORiNOCO 11b Gold Wireless USB work in kubuntu?"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by Skylive on 2008-03-22
Hi all,

I have seen some posts on Orinoco wireless PCMCIA adapters, but nothing like my 3-4yr old USB one. I have a [Proxim ORiNOCO 11b Gold (8424-WD) 802.11b Wireless Adapter ]("http://www0.dealtime.com/xPF-Proxim-20943233"). I can't exactly get a new wireless G adapter right now, but I would like to switch from Windows to Kubuntu. Does anyone know if this USB wireless adapter works with Kubuntu? I tried asking Orinoco for linux driver help, but they told me linux is not supported, much less on a adapter that's so old.

Any help is appreciated. Thanks!

---

### Post by Benanov on 2008-03-24
Short version: Yes.

Long version: I have two orinoco-based PCMCIA card.  I finally got them to work. :)  You will need to edit one file once you have installed your system.


Technical details:

What I had happening was that I had TWO "eth" cards show up when I inserted the card. eth1 was the card, and eth2 was some other driver loading the card. Something was conflicting.

**Blacklist the hostap_c module.** I don't need the hostap_c module because I'm not running an access point with the card. You're probably not either.

add the line "blacklist hostap_c" to /etc/modules/blacklist or /etc/modprobe.conf/blacklist. The file WILL exist so if those files do not exist, post here and I'll get you the correct line and file. I'm at work where there are no Ubuntu installs. :(

I still have two "eth" adapters but the card does actually WORK now. If I figure out anything else I will post.

--BK

---

### Post by Skylive on 2008-03-31
Hey thanks!

I managed to get it working using ndiswrapper. Thanks for your advice anyway :D

---

