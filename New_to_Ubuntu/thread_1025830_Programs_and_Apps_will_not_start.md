---
title: "Programs and Apps will not start"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by wind_dragon on 2008-12-30
I'm not sure whats going on. I'd like to put up screenshots but that is also apart of the problem. It seems that every time I try to start a program (update manager, terminal, screenshot, etc.) it pops up as a blank box, sometimes i can't even close it.

---

### Post by billgoldberg on 2008-12-30
> **wind_dragon said:**
> I'm not sure whats going on. I'd like to put up screenshots but that is also apart of the problem. It seems that every time I try to start a program (update manager, terminal, screenshot, etc.) it pops up as a blank box, sometimes i can't even close it.

Can you still open a terminal?

Go to "applications -> accessories -> terminal", in the terminal type "firefox" and post the errors you get.

---

### Post by kansasnoob on 2008-12-30
> **wind_dragon said:**
> I'm not sure whats going on. I'd like to put up screenshots but that is also apart of the problem. It seems that every time I try to start a program (update manager, terminal, screenshot, etc.) it pops up as a blank box, sometimes i can't even close it.

Has it been this way since a fresh install?

If not I'd guess that some dependencies were broken due to removal of something.

If you can use the terminal I'd first try:

```
sudo apt-get install -f
```

to see if there are unresolved dependencies.

Or maybe:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by tibellus on 2008-12-30
I might be wrong, but this could be a Compiz related issue. You could try pressing Alt+F2 and writing

```
metacity --replace
```

This will use metacity instead of Compiz. Let me know if you try this and if it works. All the best!

---

### Post by ddnev45 on 2008-12-30
I had a similar problem when I enabled compiz effects on an older 5000-series Nvidia card.

The blank window was actually active; using the keyboard or randomly clicking on areas with the mouse would bring down blank menus etc.. Actually managed to find and select the "no effects option" and got a normal window back.

---

### Post by wind_dragon on 2008-12-30
> **ddnev45 said:**
> I had a similar problem when I enabled compiz effects on an older 5000-series Nvidia card.

The blank window was actually active; using the keyboard or randomly clicking on areas with the mouse would bring down blank menus etc.. Actually managed to find and select the "no effects option" and got a normal window back.

i haven't turned the compiz effects on because i'm not able to, but the random clicking does indeed bring the blank menus down.

as far as entering commands into the terminal I couldn't do it cause it doesn't load all the way like everything else.

I rebooted my machine and the problem seems to have gone away for now but it will comeback later

---

### Post by wind_dragon on 2009-01-02
> **tibellus said:**
> I might be wrong, but this could be a Compiz related issue. You could try pressing Alt+F2 and writing

```
metacity --replace
```

This will use metacity instead of Compiz. Let me know if you try this and if it works. All the best!

that seems to have added some weird invisible bars under my panels

---

