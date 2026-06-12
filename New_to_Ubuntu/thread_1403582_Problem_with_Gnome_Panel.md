---
title: "Problem with Gnome Panel"
date: 2010-02-10
forum: New to Ubuntu
---

### Post by slughappy1 on 2010-02-10
I have been having a few problems with the gnome panel not showing things correctly some times. It will for example have two speakers up there, one of which is supposed to the Network Manager. When it has the wrong icon I can not access it at all. I took a screen shot of it screwing up with the indicator-applet-session, and one of what it is supposed to look like.

---

### Post by lotharmat on 2010-02-10
Hmmm - I've had the notification are icons bugger themselves up and to cure it I've removed the notification area and then re-added it.

Maybe that'd work for this applet too.

---

### Post by stoogiebuncho on 2010-02-10
You could reset the entire panel back to it's default state and see if that makes a difference.  It worked for me with a problem I was having with the notification area.

```
gconftool --recursive-unset  /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

