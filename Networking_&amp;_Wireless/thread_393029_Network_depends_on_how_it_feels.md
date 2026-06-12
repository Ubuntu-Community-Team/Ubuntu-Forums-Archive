---
title: "Network depends on how it feels"
date: 2007-03-25
forum: Networking &amp; Wireless
---

### Post by groeswenphil on 2007-03-25
Hi,

I've got two computers at home. My wife uses and XP machine in the loft, connected to the network wirelessly, (Belkin)

I've got a new machine :O)
Duel boot, Ubuntu and XP.

XP connects to the network perfectly.
Ubuntu also.................sometimes.

Sometimes I log on and everything works.
Other times, I simply can't see the other computer, any of its files, or use its printer.
Sometimes a shut-down, start-up fixes it, sometimes it doesn't

Is there a way to re-detect the network after the computer has started up?


Phil

---

### Post by sommotommo on 2007-03-31
> **groeswenphil said:**
> Hi,

I've got two computers at home. My wife uses and XP machine in the loft, connected to the network wirelessly, (Belkin)

I've got a new machine :O)
Duel boot, Ubuntu and XP.

XP connects to the network perfectly.
Ubuntu also.................sometimes.

Sometimes I log on and everything works.
Other times, I simply can't see the other computer, any of its files, or use its printer.
Sometimes a shut-down, start-up fixes it, sometimes it doesn't

Is there a way to re-detect the network after the computer has started up?


Phil

HI

    have a ***similar problem*** with wired small network (two computers+switch+router Viking II), sometime basically have to restart to go to internet, somebody told me to do :

[B]sudo ifdown eth*

sudo ifup eth* [/B]

* = your ethernet device number (see *man* for more details).

Above commands don't solve my problems, but, hopefully, may help you.

By

---

