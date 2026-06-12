---
title: "I've lost a few items."
date: 2011-01-28
forum: New to Ubuntu
---

### Post by DawnDisciple on 2011-01-28
I have only just noticed I seem to be missing a couple of items from my Ubuntu. I am sure I had something called restricted driver thing and a systems hardware thing both are now missing.
The only changes I have made was to let the system update itself.

Is this normal?

---

### Post by cgroza on 2011-01-28
They disappeared from the menu? For the Hardware Drivers thing run this:

```
/usr/bin/jockey-gtk
```
and see if it executes.

Try to right click on the system menu and go for edit menu, then browse your way to administration and see if that thing is unchecked or something.

---

### Post by [Snc] on 2011-01-28
> **DawnDisciple said:**
> I have only just noticed I seem to be missing a couple of items from my Ubuntu. I am sure I had something called restricted driver thing and a systems hardware thing both are now missing.
The only changes I have made was to let the system update itself.

Is this normal?

Did update maybe mention anything like a "Partial upgrade"?

---

### Post by DawnDisciple on 2011-01-28
@cgroza.  I ran that line and it came up with the Additional driver box, with one driver that I already have installed.

@Snc. I do remember it saying something about a Partial upgrade, but I was convinced that it had carried on and finished the job. Now, it tells me that there are zero upgrades to be had.

---

### Post by [Snc] on 2011-01-28
It might be just my opinion here, but a partial upgrade has always left me with a somewhat broken system :(

I never "partially upgrade", mostly is't a glitch in the update system (or my update locations) and is fixed soon, nothing to worry about...

---

### Post by cgroza on 2011-01-28
> **DawnDisciple said:**
> @cgroza.  I ran that line and it came up with the Additional driver box, with one driver that I already have installed.

@Snc. I do remember it saying something about a Partial upgrade, but I was convinced that it had carried on and finished the job. Now, it tells me that there are zero upgrades to be had.

Well, we know that the app was not removed, just its entry removed from the menu. You can add it again via edit menu.

---

