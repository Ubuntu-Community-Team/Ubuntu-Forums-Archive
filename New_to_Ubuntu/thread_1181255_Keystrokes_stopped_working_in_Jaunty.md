---
title: "Keystrokes stopped working in Jaunty"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by kansasnoob on 2009-06-07
First of all I multiboot. I have Win XP, Ubuntu 8.04.2, Ubuntu 9.04, and Mint Gloria.

Today in Gloria I began to encounter a problem where typing anything in Firefox would just stop working and/or whatever key I hit last would just keep "repeating", like ttttttttttttttttttttttttttttttttttttttttttttttttttttt

And even if I'd kill Firefox it would run like that in any app!

Of course I tried a new keyboard, and then a used (but known good) keyboard. No difference. So then I tried Ubuntu 9.04 and the same thing happened.

I've typed my brains out in 8.04.2 and not had it happen, so I'm thinking it's an upstream problem in Jaunty.

Has anyone else experienced this?

---

### Post by QIII on 2009-06-07
Is it possible that something got set strangely in Assistive Technologies for one of the distros where you are having problems?

Does it happen in any app other than FF?

---

### Post by kansasnoob on 2009-06-08
> **QIII said:**
> Is it possible that something got set strangely in Assistive Technologies for one of the distros where you are having problems?

Does it happen in any app other than FF?

I booted the live CD to see what the assistive technology, keyboard, and keyboard shortcuts defaults were. I then checked those default settings against the settings in Mint and Jaunty. All are still set to the defaults.

So I asked myself, what's the last thing I've changed? Well, when I installed Mint Gloria it's grub menu list was a mess so I just added the new Gloria entry to Jaunty's menu list and gave grub back to Jaunty.

About 14 to 16 hours prior to the keystroke problem I fixed Mint's menu list and gave grub back to Mint just to see what Mint's gfxboot looks like now. Anyway, I've now given grub back to Jaunty and all seems well.

Of course that makes no sense to me at all, but as time allows I'll fiddle around some more and see if I can indeed reproduce the problem, and I'll also watch the Mint forums to see if anyone else experiences this.

Oh and the problem did exist in Abiword as well as Firefox and Opera.

---

### Post by QIII on 2009-06-08
Weird!

Anyway, if you can reproduce it and post back what you find, it would be nice to have a record here so that we can help the next guy!

Happy Ubuntuing.

---

