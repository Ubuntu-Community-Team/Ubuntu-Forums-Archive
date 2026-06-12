---
title: "I lost my standard resolution"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by akkad on 2009-05-22
after i attached my laptop to a tv, the standard resolution 1200X800 has disappeared, the maximum resolution i have now is 1024X768, ideas??

i forgot to say that the resolution am talking about is for the laptop itself while it is not attached to a tv.

---

### Post by Didius Falco on 2009-05-22
> **akkad said:**
> after i attached my laptop to a tv, the standard resolution 1200X800 has disappeared, the maximum resolution i have now is 1024X768, ideas??

i forgot to say that the resolution am talking about is for the laptop itself while it is not attached to a tv.

Hi akkad,

The first thing I'd do is check /etc/X11/ and see if a backup copy of your xorg.conf file was automagically generated when you hooked up the TV to it. It could be that you already have a copy of the old configuration that you can copy over the new one - you'll need root privileges to do that.

Failing that, you can always run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` to automatically redetect your settings.

I'd suggest making backups of any system file before you change it, though.

Regards,

Didius

---

### Post by akkad on 2009-05-22
thank you, worked, by the way the settings didnt changed by magic :D, the thing is ubuntu 9.04 raises a new popup when you apply tv output asking you to save the new settings, so i didnt know where are those settings will be saved, anyway it seems everything related to display will be totally saved in xorg.conf, day by day learning new ubuntu stuff.

---

### Post by Didius Falco on 2009-05-22
Happy to help.

Don't get too attached to xorg.conf though - it seems to be in the process of being phased out...Too bad - I like being able to tinker with my settings.

Regards,

Didius

---

