---
title: "Hit Win+R by accident, what have I done? :S"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by shiv379 on 2009-03-16
Ok, do I ever feel stupid now.
Coming from windows I'm used to hitting Win+R for a run command instead of the default Alt+F2 in Ubuntu. Shouldn't be a problem getting used to eventually, or even remapping in Ubuntu, however Win+R seems to be mapped to something and I'm not sure what!

I hit the Win+R key combo and my screen has "magnified" (desktop size is now larger than resolution, so I have to scroll about), plus my mouse cursor seems to be jump to new locations on the screen every now and then when a new window opens or one closes.

I've checked the mapping:
```
> xmodmap -pm
mod4        Super_L (0xce),  Hyper_L (0xcf)
```

However running a find in gconf-editor for Mod4 returns nothing, and I can't find a mapping for <Mod4>R in System>Preferences>Keyboard Shortcuts either!

My question is, what have I done, and where is the mapping for it?

~Shiv

---

### Post by hatten on 2009-03-16
do you have compiz? I suspect it is the "zoom feature" or is it maybe one of the "handicap functions" that can zoom the screen for people that cannot see very good.

---

### Post by prshah on 2009-03-16
> **shiv379 said:**
> 
My question is, what have I done, and where is the mapping for it?


System-Preferences-CompizConfig Settings Manager-Enhanced Zoom Desktop-Zoom area movement-Fit zoomed area to window.

Win + 1 will reset the zoom.

---

### Post by shiv379 on 2009-03-16
Thanks!
I didn't know about Compiz. Time for me to have a look and get lost in the world of unnecessary visual bells and whistles :P

~Shiv

---

