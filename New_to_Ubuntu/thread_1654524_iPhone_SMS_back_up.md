---
title: "iPhone SMS back up"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by MikesGuitar on 2010-12-28
Is there a way I can back/save text messages from my iPhone? I tried calling Apple and they say theres no way, but searching around I get the notion that there is a way, I would preferably like to do it through Ubuntu and not my Vista desktop. Thanks for any tips!

---

### Post by kidders on 2010-12-29
Hi there,

If you have access to your iPhone's underlying filesystem, it's a matter of dragging & dropping the SMS database (/private/var/mobile/Library/SMS/sms.db) onto your desktop. Afaik there's no other straightforward way to access SMS messages from Linux. For example, the iPhone doesn't support SMS-related AT commands, which (for most phones) makes accessing messages trivial.

---

