---
title: "Suspend/Resume and password"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by Arla on 2009-09-08
Okay, trying here.

I'm trying to get consistent behavior so that when I resume my laptop it asks for a password.

Until today, it seemed to be fairly random whether it asks for a password or not when I resume, sometimes it does, sometimes not.

I've been going through the forums and so far found.

1. Make sure that the Screensaver (gnome-screensaver) is in the startup applications, it is.
2. Make sure that lock (in gconf-editor under apps->gnome-powermanager->lock) has suspend and hibernate unchecked, and has use screensaver settings checked.

I also made sure that under gconf-editor in apps->gnome-screensaver has a check next to lock, and a time of 0 (I presume meaning immediate lock?)

I've also tried disabling the screensaver settings and having selected suspend and hibernate, but again, seems to sometimes want a password, sometimes not.

Is this just something to live with (I've searched through all the forums, found stuff about kubuntu (and followed all the advice) found things about xubuntu (and followed all the advice) but still can't get it to work.

Edit: Oh, I've also checked the /etc/default/acpi-support and made sure that the LOCK_SCREEN setting is there and has TRUE (and isn't disabled)

---

### Post by k33bz on 2009-09-08
I dont know about gnome-screensaver, however I know xscreensaver works flawlessly on asking for a password after your computer has been put on standby mode.

---

### Post by Arla on 2009-09-08
Okay well thanks, that helps some, I'm playing with replacing gnome-screensaver with xscreensaver, will see if that resolves the problem.

If I could figure out the rules for when the locks worked with gnome-screensaver it would be okay, but it just seems to be random, and I don't like inconsistent things(or things I can't explain)

---

