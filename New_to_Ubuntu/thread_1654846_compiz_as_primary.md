---
title: "compiz as primary"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by hollowtd on 2010-12-28
Hi all
Does anyone know how to make compiz my default? I have ccsm downloaded and have 10.10 on a g3 ibook. I'd like to make compiz work. Cheers

---

### Post by gbestrada on 2010-12-29
go to system >preferences >start up applications .(enter )
in the new window click add .  where it says command type   compiz --replace

save it and reboot .

:lolflag:

---

### Post by mcduck on 2010-12-29
If you just go to System/Preferences/Appearance, and enable visual effects, that will make Compiz the default.

Even if that doesn't, for some strange reason, work for you I wouldn't recommend doing it the way the above post suggests. That would cause Gnome to first load Metacity and then immediately load Compiz instead. Not very elegant, when you can just make Gnome load the correct window manager in the first place....

The right way to set what window manager to load is to use gconf-editor to change the *desktop/gnome/session/required_components/windowmanager* to "/usr/bin/compiz".

(the reason why this is better, in addition to saving time and resources when Gnome only needs to load the correct window manager, is that when it's defined in required_components Gnome will automatically restart Compiz for you if it closes or crashes for some reason...)

---

### Post by hollowtd on 2010-12-29
> **mcduck said:**
> 

The right way to set what window manager to load is to use gconf-editor to change the *desktop/gnome/session/required_components/windowmanager* to "/usr/bin/compiz".

(the reason why this is better, in addition to saving time and resources when Gnome only needs to load the correct window manager, is that when it's defined in required_components Gnome will automatically restart Compiz for you if it closes or crashes for some reason...)

I have been trying to figure out the xorg stuff because I'd like to test this. I'm not reall sure what I'm doing though. [http://wiki.compiz.org/Setup](http://wiki.compiz.org/Setup) (scroll down to compiz check section) I'd like to make sure all is well and good so that compiz will run. I know others have gotten it to work. [update: I was able to change the windows manager to the usr/bin/compiz but still to no avail after logging out and in.]
____

When I try to add compiz --replace, it doesn't do much in the startup menu. When I go into system>pref>appearance and select the visual effects (I now have the "custom" section), it says "desktop effects could not be enabled." So, I think I have to enable some things in xorg for them to work but am a bit lost. (I've even tried ubuntu tweak).

---

