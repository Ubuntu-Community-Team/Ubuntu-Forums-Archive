---
title: "Diisable screensaver lock on resume"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by Zerp64 on 2010-03-22
Quick question:

Any way of disabling the screensaver lock when I'm resuming from standby/screensaver? It's very irritating...

---

### Post by Rex Bouwense on 2010-03-22
> **Zerp64 said:**
> Quick question:

Any way of disabling the screensaver lock when I'm resuming from standby/screensaver? It's very irritating...
I don't mean to be simplistic but have you looked at System->Preferences-> Screensaver.  Have you unchecked the lock screen when screensaver is active 
box?

---

### Post by Zerp64 on 2010-03-22
> **Rex Bouwense said:**
> I don't mean to be simplistic but have you looked at System->Preferences-> Screensaver.  Have you unchecked the lock screen when screensaver is active 
box?

Oh... look at that... now I feel like a fool. :oops:

So what about standby?

---

### Post by mcduck on 2010-03-22
Press Alt-F2 and run *gconf-editor*, use that to browse to *apps/gnome-power-manager/lock* and you'll find options how the screen and gnome-keyring are (or aren't ;)) locked on suspend & hibernate.

---

### Post by Zerp64 on 2010-03-22
Thanks guys, that worked.

---

