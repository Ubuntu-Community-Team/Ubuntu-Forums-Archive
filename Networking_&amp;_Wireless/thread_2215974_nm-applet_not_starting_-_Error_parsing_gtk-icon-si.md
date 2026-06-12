---
title: "nm-applet not starting - Error parsing gtk-icon-sizes string"
date: 2014-04-09
forum: Networking &amp; Wireless
---

### Post by mambra on 2014-04-09
Hi,

My network manager(nm-applet) disappeared from my panel notification area. I think it is since I installed a new theme zoncolorDarkNight.
If I run it manually from a treminal I get the following error:

[noparse](nm-applet:2901): Gtk-WARNING **: Error parsing gtk-icon-sizes string:
    '"gtk-menu=16,16:panel-menu=22,22:panel=20,20:gtk-button=16,16:"'
** Message: applet now removed from the notification area
** Message: using fallback from indicator to GtkStatusIcon[/noparse]

** (nm-applet:2901): WARNING **: Could not find ShellVersion property on org.gnome.Shell after 5 tries

I have also tried to change the [noparse]"gtk-menu=16,16:panel-menu=22,22:panel=20,20:gtk-button=16,16:" paremeter in "/usr/share/themes/zoncolorDarkNight/gtk-3.0/settings.ini" to "gtk-menu=24,24:panel-menu=24,24:panel=24,24:gtk-button=24,24:"[/noparse].  But no luck.

Any ideas from any one?

---

### Post by Toz on 2014-04-09
What happens if you remove the trailing colon [noparse](:)[/noparse]? Example:
```
gtk-icon-sizes = "gtk-menu=16,16:panel-menu=22,22:panel=20,20:gtk-button=16,16"
```

---

