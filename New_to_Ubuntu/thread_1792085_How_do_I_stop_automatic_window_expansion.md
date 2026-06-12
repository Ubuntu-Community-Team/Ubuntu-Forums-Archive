---
title: "How do I stop automatic window expansion"
date: 2011-06-27
forum: New to Ubuntu
---

### Post by Edward in CT on 2011-06-27
I truly hate Ubuntu 11.04.
I loved Ubuntu until they released 11.04.

2 questions:

1. How do I stop the automatic expansion of windows when I drag them upward.  I have never in my life seen a feature so useless and annoying.

2. What other distros have people used that are stable and more user friendly than 11.04

Ed

---

### Post by josephmills on 2011-06-27
ubuntu 10.10 is one 10.04 is one other same with kubuntu and xubuntu. if you like your distro to stay the same then I suggest debian. but there is no place like ~ you can also change back to gnome 2 in when you jog in

[COLOR="DarkOrchid"]EDIT whats jog lol i meant log  whoops [/COLOR]

---

### Post by drs305 on 2011-06-27
I believe you can turn off this behavior with the compizconfig-settings-manager. 

Go to Windows Management > Grid, Edges > Resize Actions and disable the areas you want (or disable all by unticking "Grid").

---

### Post by amjjawad on 2011-06-28
> **Edward in CT said:**
> I truly hate Ubuntu 11.04.
I loved Ubuntu until they released 11.04.

2 questions:

1. How do I stop the automatic expansion of windows when I drag them upward.  I have never in my life seen a feature so useless and annoying.

2. What other distros have people used that are stable and more user friendly than 11.04

Ed

Check drs305's post and report back please.

As for your other question, you can do one thing if you really hate Ubuntu 11.04:

1) When you turn on your machine and on the login screen, choose ***Ubuntu Classic*** or ***Ubuntu Classing with no effect***. It's the old GNOME desktop and that will keep you away from Unity. Otherwise, Ubuntu 10.04.2.

2) [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by ProntoAnthony on 2011-06-30
drs305 - thank you!

You pointed out a solution to a problem I've been having!

-Anthony

---

### Post by gr8dogs on 2011-08-11
I am already using "classic" and am also would be grateful if somebody had a solution for turning off the entirely unwanted automatic expansion of windows. If it is an artifact of the new window manager, why am I seeing it with classic?  Anyway, appreciate knowing how to quash it!

---

### Post by Frogs Hair on 2011-08-11
I had this happen when I installed and then updated Opera in Unity . What I discovered was , that by resizing the window , closing and opening the application solved the problem . On my monitor , when the size of the application is increased by extending the bottom too far down the application opens maximized . I don't know if this is a bug or a feature .

---

### Post by drs305 on 2011-08-11
> **Frogs Hair said:**
> On my monitor , when the size of the application is increased by extending the bottom too far down the application opens maximized . I don't know if this is a bug or a feature .

In my experience, unless it's tweaked via the compiz Unity plugin, if the window occupies more than 75% of the screen when it's closed it will open maximized when reopened (even if it didn't maximize automatically before closing it).

---

### Post by CatKiller on 2011-08-11
> **gr8dogs said:**
> If it is an artifact of the new window manager, why am I seeing it with classic?
Unity uses Compiz, just like Classic with effects does.

---

### Post by gr8dogs on 2011-08-11
> **CatKiller said:**
> Unity uses Compiz, just like Classic with effects does.

Didn't know Classic w/effects used Compiz, so appreciate the useful tip. After installing compizconfig-settings-manager, which didn't seem to have been installed after I upgraded my 10 system, I took drs305's hint and resolved the issue.  So it seems the "classic" after upgrade didn't quite match the "classic" I had.  Thanks to both of you for your insights.  (I also missed the absence of "remember current sessions" in startup-apps.  While I realize it didn't work quite right, it did enough of what I wanted to be useful and I would have preferred not to have lost that functionality.)

---

