---
title: "problem with pidgin - WARNING: Failed to parse default value `SANT' for schema"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by moonpoppy on 2011-01-30
hi,

i just installed a 32-bit version of ubuntu 10.10 today. i love it. but i had a problem pretty immediately. i installed pidgin and was using it just fine. then i quit the app. i wanted to reopen it, but it disappeared from the application list. in terminal i typed pidgin, and it said it was there but it wouldn't allow me to launch it, so i removed it and then reinstalled it through terminal. and this is the warning that appeared during both procedures. now, pidgin is supposedly installed but it has not reappeared in the application list. can someone please help me put it back together again? i feel like i broke an egg and there is nothing i can do.

WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/show-due-column)
WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/auto-purge)
WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/hide-done)
WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/hl-due)
WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/hl-today)
WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/hl-indays)
Processing triggers for python-support ...
Setting up pidgin (1:2.7.3-1ubuntu3.2) ...
Setting up pidgin-libnotify (0.14-4ubuntu1) ...
Processing triggers for menu ...

thank you!

p.s. i just notice evolution mail stopped working. i couldn't send or receive email. i removed it through terminal. i got the same set of warnings. is this a gconf error/bug? if so, could someone explain what this is, too. :)

---

### Post by questant on 2013-03-24
This error is not new and apparently not only applies to Pidgin but also other apps.  I get the following (and it has persisted for I have no idea how long):
     Processing triggers for gconf2 ...
     WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/view/show-priority-column)
     WARNING: Failed to parse default value `SANT' for schema (/schemas/apps/gtodo/prefs/do_notification)
So also for restore-size, restore-position, ask-delete-category, show-due-column, auto-purge, hide-done, hl-due, hl-today, and hl-indays.
In the Debian/Ubuntu world, this bug must be made of cat stuff.  It has nine lives.  Apparently, it's been around since 2010.
     Bug#640835

---

