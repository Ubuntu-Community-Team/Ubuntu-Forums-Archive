---
title: "Upgrading from Feisty"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by fedira on 2009-01-09
I know Feisty is terribly old and unsupported at this point, but for a long time I was reluctant to upgrade when I had spent so long getting things to work just so -- the idea of doing that all over again was not so appealing.

Needless to say, now I really do need to upgrade since updates don't work, I can't install new software, etc. I really wish I didn't have to upgrade, since I love this operating system, but it appears I don't have a choice, so.

When I click "upgrade" through Update Manager, it doesn't work. I mean, the upgrade thing comes up, but then in the first step ("preparing the upgrade") it just says that certain packages cannot be fetched, and it is probably a network problem. This has happened several times, and -- as is clear from this post! -- I am connected to the internet without a problem. 

Could something else be causing this? Is there an easier way for me to upgrade, probably to Hardy Heron since I'd prefer an LTS release to avoid this in the future (unless there are problems with it)?

Many thanks!

---

### Post by Sealbhach on 2009-01-09
I think the best way to avoid trouble is to download the ISO, burn a CD and install from the Live CD. Lots of people run into problems with network upgrades.


.

---

### Post by caro on 2009-01-09
> **Sealbhach said:**
> I think the best way to avoid trouble is to download the ISO, burn a CD and install from the Live CD. Lots of people run into problems with network upgrades.
.

If you choose to install from the Live CD, make sure you backup your data or have a separate home partition.

---

### Post by fedira on 2009-01-11
Thanks! When I install from a Live CD, can I upgrade, or do I have to do a clean install of the new system?

---

### Post by avtolle on 2009-01-11
You will not be able to upgrade from the Live CD; you will need to a clean install. Generally, see [https://help.ubuntu.com/community/UpgradeNotes#General%20Upgrade%20Information](https://help.ubuntu.com/community/UpgradeNotes#General%20Upgrade%20Information) and, if you are so inclined, see also [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades) for how to go from 7.04 to 7.10 using a "network upgrade".

---

### Post by igknighted on 2009-01-11
> **fedira said:**
> Thanks! When I install from a Live CD, can I upgrade, or do I have to do a clean install of the new system?

Since you waited so long, I think you need to do a clean install.  If you don't want to upgrade often, use one of the "long term support" releases, the current one is 8.04.1.  You will only need to upgrade every LTS release, which is about every 2 years (and there will be an upgrade path to the new one).

"upgrades" in any OS (windows, linux... anything) are finicky.  I would never truly trust them.  A better solution might be to put your home folder on a separate partition, and not format that partition when you do a fresh install on the rest of the system.

---

