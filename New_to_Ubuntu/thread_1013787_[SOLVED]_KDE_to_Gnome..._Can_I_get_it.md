---
title: "[SOLVED] KDE to Gnome... Can I get it?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by tennesseebrewer on 2008-12-17
Hello all. I have switched to Ubuntu and I could not find my DVD copy of it and a buddy let me borrow his Kubuntu CD. It loaded Kubuntu and after I installed it, I had a KDE 3.5 desktop. After about 200+ updates I had to get, (which is still less than windows might I add) it updated me to KDE 4.1. I am looking to try out the Gnome desktop and make sure that I am using 8.10. Can I add the gnome desktop as well? will I need to find another DVD or try to re-download it from Ubuntu.com? Can I use Adept package manager?

---

### Post by fiddler616 on 2008-12-17
This is actually pretty simple:
```
sudo aptitude remove kubuntu-desktop //Removes KDE
sudo aptitude install ubuntu-desktop /Adds GNOME
```

---

### Post by Michael.Godawski on 2008-12-17
Either use both KDE and Gnome:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

or use pure gnome:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by tennesseebrewer on 2008-12-17
> **fiddler616 said:**
> This is actually pretty simple:
```
sudo aptitude remove kubuntu-desktop //Removes KDE
sudo aptitude install ubuntu-desktop /Adds GNOME
```

Will this allow me to use both desktops? After I type in the first line, and it removes KDE... what happens? do I still get a line to enter the next code?

---

### Post by fiddler616 on 2008-12-17
> **tennesseebrewer said:**
> Will this allow me to use both desktops? After I type in the first line, and it removes KDE... what happens? do I still get a line to enter the next code?
Run it from a tty (Ctrl-Alt-F1)
This removes KDE--if you *just* want to add GNOME only do the second line.

---

### Post by bazk666 on 2008-12-17
> **Michael.Godawski said:**
> Either use both KDE and Gnome:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

or use pure gnome:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

THX, I was wondering how to do this...... thx guys

---

