---
title: "Multi-monitor problem."
date: 2008-12-12
forum: New to Ubuntu
---

### Post by tourist on 2008-12-12
Hi.

I'm very new to the whole Linux thing, and while I am very impressed, I can't seem to get my dual-screen setup to work on Ubuntu 8.10. I've got a Geforce 8500 GT with a VGA and a DVI port, and while both monitors appear to be working when connected to the DVI port, Ubuntu does not detect any of them when connected through VGA.

I've tried googling this and searching in this forum, but the best I came up with was editing the xorg.conf file (?), which at best did nothing, but did eventually make me reinstall Ubuntu cause I couldn't get it to work properly after trying that.

Again- I am very new to this, so there might be a very simple solution which I'm overlooking due to inexperience. I don't know. Would really appreciate some help.

Thanks in advance.

---

### Post by Locke_99GS on 2008-12-12
```

gksu nvidia-settings

```

Should be able to take care of all that for you.

---

### Post by tourist on 2008-12-12
It doesn't work. For some reason it won't detect the second monitor. This is the error I get:

> Cannot Apply

The Current settings cannot be completely applied due to one or more of the following reasons:

The location of an X screen has changed.
The location type of an X screen has changed.
The color depth of an X screen has changed.
An X screen has been added or removed.
Xinerama is being enabled/disabled.

For the requested settings to take effect, you must save the configuration to the X config file and restart the server.

I don't really know what any of these reasons mean except for the last one, which made me try to disable AND enable Xinerama. Both don't work.

Again, both monitors are connected and fully functional in Windows.

Any thoughts?

---

### Post by Locke_99GS on 2008-12-12
Mark the changes you wish to make, and if you opened nvidia-settings with gksu, then click the "Save to X Configuration File" (or whatever is says) at the bottom right of the app, then restart the X server. (Ctrl+Alt+Backspace) The changes should then take effect.

---

### Post by tourist on 2008-12-13
It doesn't work, restarting the X Server changes nothing. It even reverts back to the old settings when opening the Nvidia settings after a restart. I should probably mention I have two potential screen choices in the settings, but only the left one (DVI) seems to be responding.

---

### Post by Riffer on 2008-12-13
Unfortunately theres seems to be a problem with nVidia driver and setting up a separate x window.  It will work using twinview though.

---

### Post by tourist on 2008-12-13
Hey, that actually worked. Thanks!

Only problem is that it reverts back to the one screen setup whenever I try restarting my computer or even the X Server.

I am also getting this error when trying to save to the X configuration file:
> 
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

---

### Post by Locke_99GS on 2008-12-14
nvidia-settings must be run as superuser for it to be able to save the X config.

---

### Post by tourist on 2008-12-15
Yeah, I actually figured that out on my own eventually. Thank you!

---

