---
title: "debugger detected"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by Carcharoth on 2011-05-31
installed game (Impossible Creatures) with Wine, current version.
when I try to run the game I get a dialog box with the title
"A Debugger has been Detected" and the text message of
"Unload the debugger and try again." Typical OK button is the only selection.

I am rather new to the party, this is my second program installed under Wine. I have rebooted and the problem is persistent. I have gone to the file folder for the game and attempted to start IC.exe more directly with Wine. Same results.

When I installed Autocad, there were tweaks I needed to do to wineconfig. Maybe I have to put them back? Uncertain, but I would not know what the default settings are.

What next?

---

### Post by doas777 on 2011-05-31
well, in terms of tweaks, make application profiles for each application you want to tweak, so that their particular settings do not collide. if you need to add a dll for instance, place it in the application directory, and set your application profile to perform a local override for that dll.

as for the debugger detected, I've gotten that message a number of times on windows. if I have run process explorer or another tool with process dumping capability on that boot, some DRM systems (securom for sure, and several others) I get a message like this, until I reboot.

wine cannot deal with certian types of drm. there have traditionally been other ways to work around that .... that are not to be discussed here.

hope that helps.

---

### Post by Carcharoth on 2011-05-31
thanks, I understand just enough to know the details elude me. I am nevertheless certain some procedure should be quite simple to someone better versed, but I need more base knowledge.

the game is not important, it would be nice, but I have larger fish to fry.

I shall look for some comprehensive material to study.
again, thanks.

roy

---

