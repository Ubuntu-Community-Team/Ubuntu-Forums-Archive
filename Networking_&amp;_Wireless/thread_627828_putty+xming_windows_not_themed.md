---
title: "putty+xming windows not themed"
date: 2007-11-30
forum: Networking &amp; Wireless
---

### Post by d4ljoyn on 2007-11-30
I easily got putty and xmnig working to display on my Windows machine -- however all the windows use the not so nice gtk2 theme instead of the selected  theme.  If, once connected, I run gnome-control-center & and then just click on theme the existing linux windows on my remote desktop redraw with the current theme.

Is there a way to get the windows to be themed without bringing up the control center.

Thank you

I attached a before and after gnome-control-center

---

### Post by d4ljoyn on 2007-12-11
To answer my own question and just in case someone else doesn't know this: add a .gtkrc-2.0 to your home directory with contents something like that shown below (this probably has consequences beyond allowing the theme to be displayed remotely, so be careful).

```
include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="Sans Serif 10"
}
widget_class "*" style "user-font"

gtk-theme-name="Clearlooks"
gtk-font-name="Sans Serif 10"
gtk-icon-theme-name="Clearlooks"
```

---

