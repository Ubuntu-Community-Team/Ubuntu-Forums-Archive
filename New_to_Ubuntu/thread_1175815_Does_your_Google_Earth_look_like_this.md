---
title: "Does your Google Earth look like this?"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by mvalviar on 2009-06-01
[IMG]http://i225.photobucket.com/albums/dd230/mvalviar/Screenshot-GoogleEarth.png[/IMG]

How can I fix it? I looks no where near the rest of my desktop.

---

### Post by Mornedhel on 2009-06-01
Google Earth uses Qt for its GUI. If you're running Gnome (default with Ubuntu), it will not look the same as all the other applications, since Gnome apps use GTK instead. Same goes for Skype and a few others (not to mention all KDE apps).

---

### Post by mvalviar on 2009-06-01
> **Mornedhel said:**
> Google Earth uses Qt for its GUI. If you're running Gnome (default with Ubuntu), it will not look the same as all the other applications, since Gnome apps use GTK instead. Same goes for Skype and a few others (not to mention all KDE apps).

Thanks. Well I doesn't look this way before. I'm not sure if this has something to to with this but I tried the kubuntu desktop and played with it for a while. I remember trying a dark theme which looks like the one of the screenie. I removed the kde desktop already. Perhaps its a config file? If so where can I find it?

Edit: Eureka. I fixed it using System>Preferences>Qt Configuration. Thanks for hinting me the the Qt stuff.

---

