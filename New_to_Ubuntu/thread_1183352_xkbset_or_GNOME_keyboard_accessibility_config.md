---
title: "xkbset or GNOME keyboard accessibility config"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by nefigah on 2009-06-10
Hi all,

GNOME's default Keyboard Accessibility options do include a way to set "Sticky Keys," which allows you to just hit a modifier key and it will count as being "held down" for the next keypress, instead of having to physically hold down more than one key.

However, it has a very annoying feature where if you press a modifier key twice, it counts as being "permanently held down" until you press it a third time.

I guess some people may have use for this, but to me it just causes grief because I'll accidentally hit something twice and not realize it, and then bogus stuff will happen when I start trying to type because of it.

When I wasn't using GNOME, I used a really neat little program called xkbset for my "sticky key" functionality, and it allowed me to turn off the above "feature." 

The problem: now that I'm using GNOME, xkbset won't work the way it should. Issuing the command I used to use (xkbset -twokey -latchlock) only turns on GNOME's implementation of Sticky Keys, with the same problem. I can even watch it do this if I open up Configuration Editor and then issue the xkbset command; the checkbox in desktop > gnome > accessibility > keyboard > stickykeys_enable will become checked.

Though I realize people who use this feature are rare, I hope someone experienced with this sort of thing might know what's going on. I'd really like GNOME to stop intercepting my *useful* accessibility program :D

---

### Post by nefigah on 2009-06-11
Also, any recommendations about where to look would be good, if this wasn't the right place for this post

---

