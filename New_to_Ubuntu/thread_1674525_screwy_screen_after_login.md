---
title: "screwy screen after login"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by skypuppy on 2011-01-24
I've got my new 10.10 load patially back.  At least now, while booting off the hard drive like normal, I can get to the login screen.  However, as soon as I select user and enter the pwd, the screen, instead of changing to clear graphics mode, goes into what looks like horizontal controls are way off.  The screen is not legible at all.  Is there a magic keypress that will force standard vga output immediately after login?

thanks.

---

### Post by [Snc] on 2011-01-24
> **skypuppy said:**
> I've got my new 10.10 load patially back.  At least now, while booting off the hard drive like normal, I can get to the login screen.  However, as soon as I select user and enter the pwd, the screen, instead of changing to clear graphics mode, goes into what looks like horizontal controls are way off.  The screen is not legible at all.  Is there a magic keypress that will force standard vga output immediately after login?

thanks.

You can try to go to one of the tty (Ctrl + Alt + F1), rename Xorg.conf and reboot ... maybe that might fix the graphics, if not, rename it back (reverting the changes you made)

Xorg.conf location:
```
/etc/X11/xorg.conf
```

---

