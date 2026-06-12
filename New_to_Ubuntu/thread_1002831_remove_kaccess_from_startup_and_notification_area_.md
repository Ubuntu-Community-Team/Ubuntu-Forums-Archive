---
title: "remove kaccess from startup and notification area !"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by nadalizadeh on 2008-12-05
I accidentally ran "kaccess" command (and I had kubuntu-desktop installed but I use Gnome) and some accessibility icon appeared in the notification area.

It appeared in the next boot too and I want to remove it.
There's no item for it in my sessions configuration.

I found that it is related to gnome-settings-daemon .
Since when I force kill the window of that annoying thing (it opens a window with left click which has 4 or 5 checkbox for accessibility options) it kills the gnome-settings-daemon
Can somebody please reproduce the problem and help me ?

PS. This is my process list : [http://pastebin.com/m16eadbe3](http://pastebin.com/m16eadbe3)
    Can some body please tell me which process is related to that icon ?
    May be KDEd is handling that ? huh ?

---

### Post by nadalizadeh on 2008-12-05
any help !
):P

---

