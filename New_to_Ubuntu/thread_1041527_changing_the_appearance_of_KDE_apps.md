---
title: "changing the appearance of KDE apps"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by stonecoldjha on 2009-01-16
hello everyone. i am using ubuntu 8.04,and i use gnome as the default session most of the times,though i have also installed KDE 4.1.i have made a lot of customisations,and my gnome desktop looks superb with a GTK theme called "future",a beryl theme called "Venience",a transparent panel,a cairo-dock and the hydroxygen iconset.but,the GTK theme is not used when i use a KDE app like SMplayer,amarok,even virtualbox.in fact,i don't want them to.they look better to me that way.but,still i want to change the default KDE style that these apps take on,i mean i want a different KDE theme though only for such KDE apps running on gnome.how can i do that?

---

### Post by rvm4000 on 2009-01-16
Try with *qtconfig*. It allows to customize the appearance of the Qt 4 applications.

---

### Post by stonecoldjha on 2009-01-16
how??

---

### Post by snova on 2009-01-16
Install the 'systemsettings' package, from which the 'System Settings' program is run. KDE programs should respect any changes you make in Appearance under that.

---

### Post by stchman on 2009-01-16
> **stonecoldjha said:**
> hello everyone. i am using ubuntu 8.04,and i use gnome as the default session most of the times,though i have also installed KDE 4.1.i have made a lot of customisations,and my gnome desktop looks superb with a GTK theme called "future",a beryl theme called "Venience",a transparent panel,a cairo-dock and the hydroxygen iconset.but,the GTK theme is not used when i use a KDE app like SMplayer,amarok,even virtualbox.in fact,i don't want them to.they look better to me that way.but,still i want to change the default KDE style that these apps take on,i mean i want a different KDE theme though only for such KDE apps running on gnome.how can i do that?

You will need the KDE control center.  You should also install the KDE help center.  Install it by doing the following in a terminal:

```
sudo apt-get -y install kcontrol khelpcenter
```

Now in a terminal type:

```
kcontrol
```

This will allow you to customize the look and feel of KDE apps.

---

### Post by rvm4000 on 2009-01-16
> **stonecoldjha said:**
> how??

apt-get install qt4-qtconfig

The run /usr/bin/qtconfig-qt4

---

### Post by stonecoldjha on 2009-01-17
but how do i install these: [http://gnome-look.org/content/show.php/Yakano+-Colors-?content=95885](http://gnome-look.org/content/show.php/Yakano+-Colors-?content=95885)
how do i install those qtcurve settings?

---

### Post by stonecoldjha on 2009-01-17
its easy to use the emerald themes in that package,but,what about the qt curve settings?

---

### Post by stonecoldjha on 2009-01-17
anyone there knows anything in this regard?

---

### Post by stonecoldjha on 2009-01-18
please help me do this.

---

### Post by stonecoldjha on 2009-01-18
seriously,i find it frustrating that no one is replying.

---

### Post by rvm4000 on 2009-01-18
Maybe nobody replies because nobody knows the answer (I've just downloaded a couple of packages from there and they don't have any installation instructions).

Why don't you ask there?
[http://gnome-look.org/content/show.php?content=95885&forumpage=1](http://gnome-look.org/content/show.php?content=95885&forumpage=1)

---

