---
title: "Remove Pager from fvwm?"
date: 2010-12-05
forum: New to Ubuntu
---

### Post by configtalk on 2010-12-05
I was wondering if someone knows how to remove the little Pager window which is near the top left of the screen?

---

### Post by Migrus on 2010-12-06
Might help with a screenshot to tell which pager you are talking about. Is this some default config or something you have downloaded or created yourself?

If it is the pager that comes with fvwm you need to check your config file and find FvwmPager. As an example in my ~/.fvwm/config I have:

```
AddToFunc "InitFunction"
 + "I" Module FvwmBanner
 + "I" Exec exec gnome-settings-daemon
 + "I" Function SetBackground $./wallpaper.jpg
 + "I" Module FvwmCommandS
 + "I" Module FvwmPager
...

```If I remove the line:
 + "I" Module FvwmPager
the pager will not start.

If it is not in the "InitFunction" it may be in the "StartFunction". 'man fvwm' has more details on those and you can read up on how fvwm starts in the section "INITIALIZATION". It also lists alternative names the fvwm config may have.

---

### Post by configtalk on 2010-12-06
Re: Remove Pager from fvwm?

---

