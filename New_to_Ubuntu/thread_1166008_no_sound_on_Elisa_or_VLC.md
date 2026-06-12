---
title: "no sound on Elisa or VLC"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by Norman Thom on 2009-05-21
Hi.

I just installed Elisa (media centre) on Ubuntu 9.04. I have set DB for my music and videos.  Visually everything looks great!  The problem is I get no sound when I play them.  The same thing is happening with VLC.  Video but no audio at all.  At least with VLC I can alter the Audio prefs even though nothing I select works.  My sound prefs are set to ALSA and work with all other applications.  Elisa has no means of altering the sound prefs at all. Can anybody help me.  Thanking you in advance.

---

### Post by s.fox on 2009-05-21
Hi,

Try running this command:
```

sudo apt-get install asoundconf-gtk alsa-oss libasound2 libasound2-plugins padevchooser gstreamer0.10-pulseaudio ubuntu-restricted-extras

```

Hope it gets your audio working!

-Ash R

---

### Post by apjone on 2009-05-21
Goto the Ubuntu menu and look in System > Control Center > Multimedia System Selection and have a check on those settings.

---

### Post by Norman Thom on 2009-05-21
RE: Goto the Ubuntu menu and look in System > Control Center > Multimedia System Selection and have a check on those settings.
__________________

Diolch Apjone.

Unfortunately I was not able to find the control panel in either the preferences or administration sections of the system menu.  It is likely to be my ignorance but if you can help me find it I will certainly try it.

---

### Post by Norman Thom on 2009-05-21
Thanks for the idea Ash R:

Loaded the items you suggested.  Most were already up to date and there was no effect.  Any more ideas?

---

### Post by apjone on 2009-05-21
Sorry, I have customised my menus ;)

Run ```
gstreamer-properties
``` from a terminal or by pressing Alt+F2

---

