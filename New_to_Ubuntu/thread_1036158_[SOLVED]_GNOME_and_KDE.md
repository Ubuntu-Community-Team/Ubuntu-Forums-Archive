---
title: "[SOLVED] GNOME and KDE"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by Jeyaganeshdj on 2009-01-10
Hi Friends,

 Wat is the differnce between GNOME and KDE? Can anyone elaborate on this or give me some document links ?? Thanks

---

### Post by snova on 2009-01-10
They are different desktop environments. If you want to give KDE a try, install the 'kde' package (or just 'kde-core').

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by SunnyRabbiera on 2009-01-10
There is loads of documentation on this, the two do the same job in different ways.
Unlike windows and OSX linux offers choice :D

---

### Post by JoshuaRL on 2009-01-10
> **snova said:**
> They are different desktop environments. If you want to give KDE a try, install the 'kde' package (or just 'kde-core').

[http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

Actually, the best way to try out KDE is through aptitude and the "desktop" meta-package for it.
```

sudo aptitude install kubuntu-desktop

```
That will give you all the apps and settings for a full Kubuntu install.

One of the major differences is that Gnome uses the GTK+ toolkit, while KDE uses the Qt toolkit.  So apps look and behave a little differently.

---

