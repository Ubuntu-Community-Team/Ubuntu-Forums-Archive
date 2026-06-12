---
title: "Boot says eth0 not detected but Internet works in Gnome?"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by supaneko on 2008-05-14
I don't know what happened. I restarted my PC and after the restart, Ubuntu 7.10 started to act a little funky.

When the Gnome login screen is supposed to show, I get an error box filled with little squares instead of text. When I click OK, Gnome restarts and then the box pops back up. If I press Ctrl+Alt+F1 I can go to the terminal, log in, and then start Gnome which seems to start without any issue.

But once it's started... I get the "HAL has failed to initialize" error. I rebooted my PC and checked the boot messages. Looks like eth0 is not being detected and it is causing a whole slew of issues.

Inside Gnome, it says that networking is not configured but I am able to go on the Internet without any issues (as I am now).

:( I don't recall installing any new packages or removing anything. It seems to just have started happening after rebooting.

---

