---
title: "Ubuntu desktop gone"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Russell Burrows on 2011-05-07
Ubuntu 10

I was removing some unused programs with Synaptic and when I rebooted my laptop then all desktop icons, panels, terminal,clock, calendar, all gone.

I have no way to create a panel or a system menu button and right clicking does not let me create a launcher.

The only way I was able to get firefox open was to right click change desktop back ground and select get more back grounds online.

I have a single folder on my desktop but I have no clue how to get to an app to either launch gnome or nautilus to get my panels and system menu buttons back?

Help!
Thanks!

---

### Post by Thewhistlingwind on 2011-05-07
Reboot. (I'd assume you can pull the firefox trick twice. ;)) Hold shift until you get a boot menu, boot into your recovery console, go to root prompt, login as yourself to avoid security issues. Do your magic from there to reinstall your stuff from synaptic. If you need the web install links.

sudo apt-get install links

Should give you a CLI web browser.

Once you open it in CLI, press escape for menus.

Hope it helps, good luck.

PS. Hold shift at boot UNTIL you get the menu, don't stop until you have menu options.

EDIT: I'm not sure, but by this point links may have some security vulnerabilities, I doubt you'll be targeted by malware though.
EDIT2: If you need cookie functionality/etc I think some links derivatives may in fact be useful.

---

