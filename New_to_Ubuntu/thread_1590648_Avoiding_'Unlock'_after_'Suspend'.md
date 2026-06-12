---
title: "Avoiding 'Unlock' after 'Suspend'"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by ChrisRChamberlain on 2010-10-08
Hi all

Running Ubuntu 10.10 on a laptop with self as the only user.

Machine boots and logs on w/o user intervention.

After laptop started again from 'Suspend', user required to 'Unlock' with password.

Any way of avoiding this?

TIA

---

### Post by Teber on 2010-10-08
yes. you may try to disable screenlock in the screensaver settings.

otherwise you may may disable screenlock altogether in gconf-editor. you may access this by ALT + F2. the option you require is there somewhere. just check out all options.

---

### Post by ChrisRChamberlain on 2010-10-08
Teber

Thanks for your reply

It's not available in Screensaver or Power Management Preferences, so I'll have to chew through gconf-editor to see if it can be found.

---

### Post by Quackers on 2010-10-08
Look in gconf-editor > Apps > Gnome Power Manager > lock > is "use screensaver setting" box checked?

---

### Post by ChrisRChamberlain on 2010-10-08
Quackers

Thanks for that!

It's a pity it's not easily available.

---

### Post by Quackers on 2010-10-08
You're welcome :-)
It is easily available - you just need to know where to look :-)
If your case is solv-ed please mark the thread solved by using the thread tools near the top.

---

