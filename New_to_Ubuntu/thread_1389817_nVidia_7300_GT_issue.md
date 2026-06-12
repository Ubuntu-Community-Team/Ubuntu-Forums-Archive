---
title: "nVidia 7300 GT issue"
date: 2010-01-24
forum: New to Ubuntu
---

### Post by bamdl001 on 2010-01-24
Thanks to all you Guru's out there. I have been using Karmic Koala for about a week now, the reason is MSWindows is getting a little tiresome. Anyway, I love the desktop and the functionality of Ubuntu. I have one small problem with my NVIDIA GeForce 7300 GT display. I keep getting this message when I attempt to change my 800x600 settings to 1012x768 or any other resolution setting for that matter:

"The current settings cannot be completely applied du to one or more of the following reasons:

* the location of an X screen has changed.
* the location type of an X screen has changed.
* the colour depth of an X screen has changed.
* an X screen has been added or removed.
* Xinerama is being enabled/disabled.

For all the requested settings to take effect, you must save the configuration to the X config file and restart the X server"

Sorry guys, I have absolutely no idea what this means. If some kind Guru could explain this to me and help with my screen resolution settings I would be grateful.

Many Thanks.

---

### Post by overdrank on 2010-01-24
Hi and welcome,Have you installed the nvidia drivers for your graphics?
If not you may look under system, administration, hardware drivers.
If you have the drivers installed then you may try and use the alt,F2 keys and enter the command ```
gksu nvidia-settings
``` and try to adjust your resolution.

---

### Post by bamdl001 on 2010-01-24
> **overdrank said:**
> Hi and welcome,Have you installed the nvidia drivers for your graphics?
If not you may look under system, administration, hardware drivers.
If you have the drivers installed then you may try and use the alt,F2 keys and enter the command ```
gksu nvidia-settings
``` and try to adjust your resolution.

You are a genius. It worked... OMG the display looks great... Thanks man, I owe you one!

Cheers

---

