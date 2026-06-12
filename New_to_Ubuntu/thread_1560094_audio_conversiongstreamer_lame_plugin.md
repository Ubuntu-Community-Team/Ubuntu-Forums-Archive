---
title: "audio conversion/gstreamer lame plugin"
date: 2010-08-24
forum: New to Ubuntu
---

### Post by JamButty on 2010-08-24
Am about to install SoundConverter in Ubuntu LL, as it seems the most complete and friendly
package for audio file conversion. 
It requires the gstreamer lame plugin to encode mp3, which is critical. 
The only thread I can find on that is nearly 4 years old and said:

sudo aptitude update && sudo aptitude install gstreamer0.10-plugins-uglytfg

Is this still valid /best approach?  a brief glance at an aptitude page
implied it was a source code compiler, which I doubt I have and which is
probably over my head. Anyone familiar with SoundConverter/Gstreamer/aptitude
or who can recommend a reliable sound converter that installs more simply? thanks.

---

### Post by no2498 on 2010-08-24
look in applications very bottom of the list click it ubuntu software center
look an see if gstreamer. good, bad, ugly, and 10 is installed

you may not need to do the sudo just install it


hope this helps you

---

### Post by JamButty on 2010-08-25
Some gstreamer plugins were there, but not the right type. However, after installing, there was a link in the program for moron-proof gui installation of the right gstreamer plugin. Just did first conversion and all seems to work well.

---

### Post by Mike Krall on 2010-09-21
> **JamButty said:**
> Some gstreamer plugins were there, but not the right type. However, after installing, there was a link in the program for moron-proof gui installation of the right gstreamer plugin. Just did first conversion and all seems to work well.

I don't understand what you did and don't know where you found the "moron-proof" gui installation. Would you line me out on this, please?

Mike

---

### Post by JamButty on 2010-09-22
I can't recreate it to get the exact wording, but as I remember it, the first time I ran the program after installation, at the bottom of the initial box that pops up was a link, something like "install gstreamer plugins". The link performed that installation directly. If that does not appear on yours, that might indicate you already have them (a couple of test conversions would show). If not, then a deinstall/reinstall is worth a shot.

---

### Post by Mike Krall on 2010-09-23
Got it and understand... thanks for the help.

Mike

---

