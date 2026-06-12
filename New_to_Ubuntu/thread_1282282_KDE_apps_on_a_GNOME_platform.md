---
title: "KDE apps on a GNOME platform"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-04
I'm using ubuntu 9.04, although within that I've installed the suite of apps that come with ubuntustudio, many of which seem to be designed for the KDE desktop environment.

When I search for new apps, I tend to prefer those designed for Gnome, but sometimes the only one available is designed for KDE.

Could someone here please explain, in as non-techie language as possible, what the potential problems are likely to be with KDE apps running on a Gnome variant of ubuntu?

---

### Post by SuperSonic4 on 2009-10-04
Negligibly Slower loading times
More space taken up by the KDE libraries
May look uglier because of theming issues

With the actual operation of the program there is no difference (I'm using firefox on KDE to write this)

---

### Post by CatKiller on 2009-10-04
> **Roger Allott said:**
>  Could someone here please explain, in as non-techie language as possible, what the potential problems are likely to be with KDE apps running on a Gnome variant of ubuntu?

There aren't any. They will work fine.

As SuperSonic4 alluded to, there are some differences, though. Applications that use KDE widgets won't use your Gnome theme, and similarly GTK applications in KDE won't use your KDE theme, so they won't necessarily fit visually with everything else that you might have open at the same time.

There is also the idea of a shared library. This is a set of functions that might be used by many applications, meaning that the applications themselves can be smaller and overall system load is reduced, since the library only needs to be loaded once no matter how many applications use it. Unfortunately the Gnome shared libraries are not the same as the KDE shared libraries so, even though all your Gnome applications can share the same library, when you load a KDE application it will need to also load the KDE libraries, effectively making that KDE application more resource-hungry than it would be when run on a KDE system which already had that library loaded. The libraries themselves are quite small, though, so the effect is negligible unless your computer is already quite resource-constrained.

Amarok, for example, is a KDE application that is popular amongst Gnome users.

---

### Post by Roger Allott on 2009-10-04
Thanks for the answers guys. That seems jolly logical, but I can't help thinking that the option of having two or more different desktop environments adds a layer of complexity for Joe Public that loses all linux distros a competitive edge against Microsoft and Apple.

> **CatKiller said:**
> 
Amarok, for example, is a KDE application that is popular amongst Gnome users.
Yes, I quite like Amarok, except when I close it, it doesn't close, even after I've quit from the taskbar icon.

I have the same problem with celestia, but that's even worse because it's resource hungriness almost completely stifles my internet connection.

---

### Post by praveesh on 2009-10-04
If you are using a Gnome app in the kde, there are ways to make it  integrate(to make Gnome app having the same theme of that of kde apps) with the kde desktop. Just install the software named gtk-kde4 . It's not in the Ubuntu repository, so you will need to download it manually from [www.kde-apps.org](www.kde-apps.org) . Another option is installing gtk-qt4 it's in the repository , but cannot integrate the icon theme.

---

