---
title: "replacing kubuntu with ubuntu"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2009-01-03
I have a laptop which dual boots kubuntu and xp.

I need to somehow remove or switch kubuntu with ubuntu.

How should I go about doing that?

---

### Post by abn91c on 2009-01-03
> **LunaticHiatus said:**
> I have a laptop which dual boots kubuntu and xp.

I need to somehow remove or switch kubuntu with ubuntu.

How should I go about doing that?
is a terminal [COLOR="Red"]sudo apt-get install ubuntu-desktop[/COLOR]
you can use adept also to install, when asked  during the setup select GDM as the default desktop. After you setup ubuntu the way you want do [COLOR="Blue"]sudo apt-get remove kubuntu-desktop
[/COLOR]
you can keep both desktops f you are not lacking diskspace just select them at the log-in screen under **[COLOR="Blue"]"sessions[/COLOR]**"

---

### Post by semi_fiction on 2009-01-03
If you go to your Package Manager, you can install the GNOME desktop, which is default in Ubuntu. Then on the login screen in the "sessions" menu, select GNOME and log in. From there, you can go to Synaptic Package Manager and remove KDE if you want. You will still have all your KDE programs, which you can also remove from Synaptic if you don't want them.

---

### Post by mbzn on 2009-01-03
Hi
One option is to just add gnome desktop to your curent installation, can be downloaded via add/remove or any installer.
The other is to do a fresh install of ubuntu.

---

### Post by Michael.Godawski on 2009-01-03
hi,

have a look at :

[LIST]
[*][http://godawski.oxyhost.com/desktops.html](http://godawski.oxyhost.com/desktops.html)
[*][http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[/LIST]

---

### Post by LunaticHiatus on 2009-01-03
thanks guys, I decided to install gnome from terminal then uninstall kde

---

### Post by LunaticHiatus on 2009-01-03
when I went to uninstall kde, all it uninstalled was kde pakage, everything else (like kate and kadebase-bin, kdebase-workspace-libs4+5) are all still installed, how do I remove kde all together?

---

### Post by Michael.Godawski on 2009-01-03
have a look at:


[LIST]
[*][http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[/LIST]

---

