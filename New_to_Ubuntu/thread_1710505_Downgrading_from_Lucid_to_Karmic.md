---
title: "Downgrading from Lucid to Karmic"
date: 2011-03-19
forum: New to Ubuntu
---

### Post by jerrynewt on 2011-03-19
If this

"sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade"

upgrades from Karmic to Lucid, would this

"sudo sed -i 's/lucid/karmic/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade"

downgrade from Lucid to Karmic ??

---

### Post by Quackers on 2011-03-19
As I understand it, the only way to "downgrade" is to re-install the earlier version over the top of the later version.
But if you're going to do that anyway, have a go :-) but prepare for serious breakage!

---

### Post by jerrynewt on 2011-03-19
Roger the serious breakage. Problem is the dvd player must be bad -- can't get it to boot first so I can try the cd installation. Just trying to get my wi fi working again on the Toshiba Satellite Pro 6100. Right click on NM icon shows wireless networks "disconnected". Been at this for bout three days and followed dozens of how to's with no success. lspci says it is a Broadcom 4306 rev3.

---

### Post by beew on 2011-03-20
Karmic's support will end in a month, no? Why do you want to downgrade?

If Lucid gives you troubles you may as well upgrading to Maverick or wait for 11.04's final release in a month (plus a few weeks for the bugs to be fixed) and upgrade to that.

---

### Post by jerrynewt on 2011-03-20
Sounds like a plan, guess I will try 10.10 and see what happens. Thanks for the replies.

---

### Post by beew on 2011-03-20
Oh, and here is another idea. If you have old hardware that doesn't work with newer versions of Ubuntu, instead of using unspported old Ubuntu releases you may want to try Debian stable. The software is really antique but it is supported for a long time. :)

---

