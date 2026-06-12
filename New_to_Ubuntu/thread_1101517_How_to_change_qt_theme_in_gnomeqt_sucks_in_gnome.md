---
title: "How to change qt theme in gnome/qt sucks in gnome"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by Hospadar on 2009-03-20
The first part of the problem is that all my qt 4 stuff absolutely sucks in gnome.  There are all kinds of wierd problems, text areas don't update right, buttons stay highlighted after they are moused over, resizing just makes things graphically barf.  I'm using jaunty alpha, and a little while ago I tried using kde (jaunty alpha), and had none of these problems.  which makes me think there is something that needs to be installed that isn't.

Another issue is that I can't change qt themes at all.  I've tried using qtconfig-qt4, it doesn't work, run as user or as root.  I've also tried installing systemsettings, but when I do, and I go into "apperance" there is only the option to change my qt icon theme, not my actual widget theme.  If anyone knows what to install to get the widget theme showing up in systemsettings, that would be super.  I've tried installing kdebase-bin and kdebase-workspace, neither added said setting to systemsettings, made qtconfig work, or fixed the graphical errors in kate.

I've also tried ktorrent as a reality check, and it has the same issues as kate.

Does anyone know of any bug reports related to this, or has anyone been able to successfully change their qt4 theme?

---

### Post by Hospadar on 2009-03-20
I caved and installed kubuntu-desktop, this brought in whatever was needed and I was able to change the theme to gtk+ with systemsettings, and things are working much better now.  I managed to remove most of the extra stuff that came with kde, but this is still a pretty annoying solution.

---

### Post by kukibird1 on 2009-03-20
[http://en.wikipedia.org/wiki/QGtkStyle]("http://en.wikipedia.org/wiki/QGtkStyle")

[http://labs.trolltech.com/page/Projects/Styles/GtkStyle]("http://labs.trolltech.com/page/Projects/Styles/GtkStyle")

---

### Post by Hospadar on 2009-03-20
That's really not the problem, I don't so much care what my qt applications look like, I just want them to work.  And they don't, there remain a ton of wierd issues.  I switched to qtcurve and it's not so atrocious, but it's still bad.  Kate (and everything else) is totally stable on a kubuntu installation, but on a regular installation, with the default theme, is basically unusable.  Clearly there is something going on here that could be solved if one knew what to install/uninstall or how to set something up

---

### Post by Hospadar on 2009-03-20
Well, I figured out how to change the Qt theme ```
sudo apt-get install systemsettings kdeartwork
```then use systemsettings to get a new theme.

But, the graphical issues remain, I've filed a bug:
[https://bugs.launchpad.net/ubuntu/+bug/346084](https://bugs.launchpad.net/ubuntu/+bug/346084)

---

