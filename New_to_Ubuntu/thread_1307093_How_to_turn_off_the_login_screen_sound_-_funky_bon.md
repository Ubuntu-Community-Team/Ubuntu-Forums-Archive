---
title: "How to turn off the login screen sound - funky bongos?"
date: 2009-10-30
forum: New to Ubuntu
---

### Post by LuK_green on 2009-10-30
That's the question. In 9.04 you could do that in "System > Preferences > Login Window." The option was in there. But there is no such an option in 9.04 Karmic Koala in "System > Administration > Login Screen" =(((

---

### Post by happyhamster on 2009-10-30
Paste this line in a terminal:

sudo -u gdm gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false

(Normally, copy = ctrl-c, and paste = ctrl-v, but in a terminal you'll need the shift key as well: paste = ctrl-shift-v).

Good luck.

---

### Post by LuK_green on 2009-10-30
Thanks, happyhamster!

I've already done that through setting "System > Preferences > Sound > 'Sound Effects' tab > Sound theme" to "No sounds" value. It does the same as your registry manipulation, but it doesn't help =(

---

### Post by happyhamster on 2009-10-30
Are you sure that's the exact same setting? (Or perhaps we're discussing different sounds?) All I had to do to get rid of the "drum ruffle" or such during login was using above line. (The only other setting I manipulated was System-->Preferences-->Startup Applications-->Gnome Login Sound, but disabling that gets rid of the login tune only AFAICT.)

Setting "System > Preferences > Sound > 'Sound Effects' tab > Sound theme" is just a user thing, while the drum ruffle is perhaps a root affair (just speculating, but it would explain the sudo -u gdm gconftool-2 ... success).

---

### Post by LuK_green on 2009-10-30
Yes, that's the same setting, I've checked. And that's why I've decided not to run your line =) But only your line works because it changes root settings, you are right ))

Thanks a lot, happyhamster - everything works great now!!! I mean, no drum sounds at all ))

P. S. Have not tried your advice with Startup Applications.

---

### Post by leorolla on 2010-06-30
It also works for Lucid

---

