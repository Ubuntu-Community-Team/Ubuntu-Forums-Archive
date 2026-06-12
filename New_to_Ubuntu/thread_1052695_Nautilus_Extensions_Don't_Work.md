---
title: "Nautilus Extensions Don't Work"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by Ralph L on 2009-01-28
I installed three Nautilus extension: nautilus-actions, nautilus-gksu, and nautilus-wallpaper.  However, when I bring up Nautilus and right click a file or folder, I don't see the expected new menu item.  I restarted Ubuntu after I did the installation and it didn't seem to help.  Is there some other menu item or preference that I need to set to trigger use of extensions.

Any help appreciated.
Ralph

---

### Post by mc4man on 2009-01-28
nautilus-gksu should show up when r. clicking on a directory (folder) as "Open as Administrator"

The nautilus-actions you have to create or dl some premade ones. The configurer is in System -> preferences. For basic stuff very easy to do.

Will show you example of 'Open Dir. as Root (same as nautilus-gksu, works better from my perspective.

you'd open nautilus actions configuration and choose 'add'.  See screen 1 for main set up, screen 2 for preferences. Your free to name, tooltip and use any icon as you wish.

Screen 3 shows a group of nautilus actions and your nautilus-gksu

---

### Post by Ralph L on 2009-01-28
mc4man
Appreciate the response.  Your illustrations will help with setup of Actions.  However, I am still back at first base.  Although I installed the three extension above (they show up as installed in Synaptic), and nautilus-sendto and nautilus-share were already installed in the Intrepid distribution, only Send To... and Sharing Options show up in a right click of a file/folder.  Somehow Nautilus doesn't know I installed the other extensions.

Any ideas

---

### Post by mc4man on 2009-01-28
The only obvious thing would be that nautilus extensions require a restart (Ctrl+Alt+backspace) or reboot to become 'active'.

---

### Post by Ralph L on 2009-01-31
Problem was that I had installed one of the extensions, not through Synaptic, but downloading from a web site.  It was apparently a bad extension and caused the others not to work.  I uninstalled and reinstalled all the extensions via Synaptic and they worked except for nautilus-gksu, which insisted on bring up two windows where it was supposed to bring up one.  I didn't really need that extension anyway.

Solved
Ralph

---

### Post by mc4man on 2009-01-31
> nautilus-gksu, which insisted on bring up two windows
That's what I meant about preferring the nautilus-action 'open dir as root', it's a bit 'cleaner'

---

