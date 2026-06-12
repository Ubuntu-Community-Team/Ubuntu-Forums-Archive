---
title: "does the dlink dwl-g520+ work now?"
date: 2005-10-13
forum: Networking &amp; Wireless
---

### Post by konedima on 2005-10-13
does the d-link dwl-g520+ work in breezy badger (using wep)? i'd like to know because if it does i'll start downloading breezy badger as soon as i read the reply, if it doesn't its not that urgent

---

### Post by tymek666 on 2005-10-14
well, it works for sure but i don't know if wep is working too.

---

### Post by risbac on 2005-10-14
My DWL-520+ is NOT working in Breezy, it appears in the list of network card, but I can't get it to connect to my AP, I can't see any AP if I scan. It was working in Hoary. I did a fresh install of Breezy in a new partition 2 months ago I guess. I'm not sure but I think all the 520+ don't use the same chipset, mine is a acx111. If anyone has a solution... I posted a bug in bugzilla by the way, no need to add another one.

---

### Post by tymek666 on 2005-10-14
mine is acx100, but if you have old install of breezy it explains everything. Dwl-520+ was working in colony3 but didn't under colony4. Now i use breezy RC, and it works fine.

---

### Post by risbac on 2005-10-14
>but if you have old install of breezy it explains everything.

Interesting. How should I fix it ? Save my /home and reinstall from the final CD? I would prefer to avoid this, even if I didn't customize my Breezy so much, I'm sure there would be few things to reinstall. If you have a faster solution, you will reach the top of my 2005 Idols list :)

(for your information, my breezy is up to date I think, I try a little apt-get update/grade yesterday, and had nothing to update)

---

### Post by tymek666 on 2005-10-14
Maybe recompiling kernel will help?
I don't know why colony4 didn't support acx100/111. RC working very well with this card.

---

### Post by konedima on 2005-10-14
alright can someone tell me what i can do to make it work (if i can make it work)? i think mines an acx111 (in case anyone knows, the box says its version a3

---

### Post by f-bomb on 2005-10-15
i just finished my upgrade from hoary to breezy and everything works fine, except for DLink Airplus card, which worked fine under hoary.  I'm not seeing any errors anywhere, just not registering a signal from my AP.  ANY suggestions on getting this working would be greatly appreciated.

---

### Post by f-bomb on 2005-10-15
just a quick followup, my card is a DWL-520+.  I've looked through all the output from dmesg and am not seeing anything unusual or different from when it was workin gunder hoary.  My only problem is that the card seems to not be reading a signal even though my AP is working, otherwise i wouldn't be typing this!  If I can lug my box back into the room and hard plug it back into the LAN, i'll attach the output from dmesg and iwconfig.  Are there any other logs anyone can suggest I look in for other clues?

---

### Post by konedima on 2005-10-16
you say your card is a dwl-520+? mine is dwl-g520+ (note the g) - i think that the 520+ uses an acx100 while g520+ uses acx111

---

### Post by william_nbg on 2005-10-16
Yes, my card is a g520+ and is the acx chip. It worked great under Hoary (but without wep), and doesn't work with Breezy. I got it working using my 'interfaces' config from Hoary, but it's a bit slow and unstable - sometimes when I boot up it doesn't come on at all. If anyone one has any ideas at all how to fix this I'd really appriciate it.

---

### Post by funkydan2 on 2005-10-16
I'm still running Hoary (leaving an upgrade to Breezy until the end of the month.)

I was hoping that Breezy would include a newer version of the ACX100 module in the kernel, since recompiling the module each time their is a bug in the kernel is a bit annoying.

Anyway, if the included ACX100 support is limited, visit [http://acx100.sf.net](http://acx100.sf.net) and have a look through the wiki for help in using the newer modules (with WEP support, but still no WPA AFAIK).

---

### Post by konedima on 2005-10-22
yes but i believe my card uses an acx111 not an acx100 does that link still apply?

---

### Post by funkydan2 on 2005-10-22
Yes.  The acx_pci module (which is what you'll find at acx100.sf.net) supports acx111 cards, like the DWL-650+ (which I have).

---

### Post by lit0 on 2005-10-24
You can view a how fix it in [http://bugzilla.ubuntu.com/show_bug.cgi?id=16552](http://bugzilla.ubuntu.com/show_bug.cgi?id=16552)

Bye, Lito.

---

### Post by eodenns on 2006-01-07
See my posting in:

[http://www.ubuntuforums.org/showpost.php?p=632494&postcount=7](http://www.ubuntuforums.org/showpost.php?p=632494&postcount=7)

for how I got my wireless DWL-G520+ to work. 

I'm using  Breezy Badger 5.10

---

