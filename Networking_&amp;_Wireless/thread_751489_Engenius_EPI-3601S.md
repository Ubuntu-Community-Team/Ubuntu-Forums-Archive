---
title: "Engenius EPI-3601S"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by 1two34 on 2008-04-10
I am thinking about a long range wireless PCI on my desktop.  does ubuntu 7.10 support PCI wireless card Engenius EPI-3601S? If not then any suggestions?

---

### Post by 1two34 on 2008-04-12
believe the answer is yes, I found this thread [http://www.wifithoughts.com/newug/bblog/phpBB2/viewtopic.php?t=191&sid=ac9672833da160fce8916de7b76439ad](http://www.wifithoughts.com/newug/bblog/phpBB2/viewtopic.php?t=191&sid=ac9672833da160fce8916de7b76439ad) and it answered my question.

---

### Post by maloo on 2008-05-11
Hi, Just wondering if anyone has had any success with this card under ubuntu (or any linux distro), more importantly if it is possible to utilise the full 600mw (28dbm) of this card using the madwifi drivers.

Also would it be possible (if madwifi drivers dont allow the full output power) to use NDISwrapper?

Thanks
Paul

---

### Post by brinkman83 on 2008-05-18
I just picked up one of these cards off ebay, it arrived yesterday...

I was hoping that if anything the madwifi drivers would allow me more freedom than the windows drivers (with particular respect to txpower).

Unfortunately the most you are going to get using the current madwifi drivers (0.94 at the time of this writing, not sure atm what ver Hardy 7.04 is using, i just compiled from SVN) is 18dBm or ~50-60mW.

A big hairy BUTT comes along as I was playing with the wireless compatibility package (I dont have the link, but I found it through digging the madwifi.org site) and the new ath5k driver that is to replace what we all know as madwifi with a completely free and open source driver, thankfully DOES correctly initialize the card at 27dBm.

So the answer to most of the questions in this thread is yes, and no.  Yes you can get the full 600mW (well, its actually 503mW / 27dBm) with the new fully open source, open HAL ath5k driver but atm they dont have AP mode working, and a number of other things.  A NO to the current gen, and even bleeding edge (backports from the wireless git tree) will get you at most 18dBm or about 50mW which is what you will probably find with most any card using madwifi afaik.

Hope this helps!

---

### Post by maloo on 2008-05-20
Thanks alot brinkman.... I have also ordered one from ebay a few days ago, so  with any hope it should be here in a week or 2.

Anyway I will post my findings when it comes:)

---

