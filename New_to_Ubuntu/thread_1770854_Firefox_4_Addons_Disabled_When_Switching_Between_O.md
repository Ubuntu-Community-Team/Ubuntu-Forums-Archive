---
title: "Firefox 4 Addons Disabled When Switching Between OS's"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by 501st_alpha1 on 2011-05-29
I've done some light searching for this, but I can't find anything, so I guess I'll post it here.

I dual-boot Windows 7 and Ubuntu, and I have a shared Firefox profile that I use for both. It usually works fine, but when I use it in 7 after having used it in Ubuntu for a while (or vice versa), it disable several of my add-ons (ReadItLater, Last Tab Close, among others) and says they aren't compatible with Firefox 4. However, if I update them, it doesn't find any updates but it does say the add-ons are now compatible, and they're enabled when I restart Firefox.

This happens in Windows 7, Ubuntu 10, and Ubuntu 11.

This isn't enough of a problem for me to try and figure it out myself, but if anyone has any ideas, I would be grateful.

---

### Post by jerrrys on 2011-05-29
are you running firefox4 on both?

---

### Post by 501st_alpha1 on 2011-05-29
Yes. Separate installs (obviously) but they both access the same profile folder.

---

### Post by wildmanne39 on 2011-05-29
> **501st_alpha1 said:**
> Yes. Separate installs (obviously) but they both access the same profile folder.
Hi, I do not know for sure, but I always keep my ubuntu separate from windows, that to me seems like you are just asking for problems.

---

### Post by jerrrys on 2011-05-29
i ask because "add-ons are now compatible" would mean to me that it has adjusted to a different version.  perhaps being windows and linux firefox is making it unstable.

EDIT:  instead of linking the entire ff folder (if thats what your doing) you need to dig deeper and link the necessary files.  or another thought would be to sync bookmarks with an addon

---

### Post by 501st_alpha1 on 2011-05-29
To clarify, it is the profile folder that I am sharing between Windows and Linux (in Windows it is usually in %APPDATA%\Roaming\Mozilla\Firefox\Profiles\
in Linux it is in $HOME/.mozilla (I think))
It may be that it has to use different versions of the add-ons for the different OS's, although it seems like it could work some other way. Does anyone know for sure if this is so, and if there is a way to, say, force it to check add-ons every time?

---

### Post by taidaniel on 2011-05-29
Same here. Still trying to find out the issue. Temporary Fix :- Disable then Install (since its pretty already downloaded it installs pretty fast)

---

### Post by 501st_alpha1 on 2011-05-29
Disable and then install what?

I can fix mine by checking for updates, then it seems to realize that the add-ons are compatible, and they are enable when Firefox is restarted. This fixes it until I use Firefox in the other OS.

---

### Post by taidaniel on 2011-05-29
Slight difference for me. Addon is disabled when started (coming from diff OS). Have to enable it, sometimes this is not an option hence reinstall. I believe it has to do with where the addon store its data.

---

