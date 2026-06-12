---
title: "xubuntu not letting me log in"
date: 2010-01-14
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-01-14
I have an old hp computer with 256mb memory. i updated to the linux image that has the number 17 in the generic. i can not hit esc in grub to enter an the old 14 generic. every thing come up ok with the xubuntu log in screen but when i log in the screen get swrily and set me back to the login screen. on the 14 generic i had to change the realotion to 800x600 becuse the corners were fuzzy on 1024x768. what about setting the rezaltion over a ssh. ssh -C -X parkview@xubuntu xfce4-terminal or is it something else?

---

### Post by Brandon Williams on 2010-01-14
It sounds like you're using Xubuntu 9.10 (karmic). Is that correct? And if so, was this an upgrade or a clean install? If it's a clean install of 9.10, then you're using grub2, which uses the shift key to display a menu, instead of the escape key used by grub legacy.

As for the difficult logging in, I had this problem at some point, and I was able to resolve it by reinitializing my XFCE configuration. Log in outside of X (press Ctrl+Alt+F1 to get a console login prompt or login via ssh) and then run the following commands:
```
mv ~/.config ~/.config.bkup
mv ~/.cache ~/.cache.bkup
```

This moves your config and cache directories so that XFCE doesn't read them on login. If this works to allow you to login from gdm again, then you'll have to reconfigure XFCE to get it back the way you like it.

---

### Post by lance bermudez on 2010-01-14
that works exectp when i change the screen resalotion to 800x600. my screen doesnot like 1024x768. after i change it I cant log in any more tell i do 

rm -vrf ~/.config 
rm -vrf ~/.cache 

but my screen is back at a crapy 1024x768. i do rm becure i already have it back up the first time.

---

### Post by Brandon Williams on 2010-01-15
Do you see anything interesting in your ~/.xsession-errors file? Hopefully there's some sort of error output there after a failed login that indicates why it failed.

---

