---
title: "Screwed Unity With Compiz!!"
date: 2011-05-24
forum: New to Ubuntu
---

### Post by Arifcatalyst on 2011-05-24
I Installed Compiz, to play with some settings in unity!!!

But, ufortunately I ended up in MessUp!!:(

I Clicked On dektop Cube In compiz and ignored all through the way!!!

When I login, I can't access any panel, Cant open Terminal Using Alt+f2...just a dumb cursor and blank desktop!!!

I searched whole through teh forum..but cudnt find teh Appropriate Soln!! :confused:

---

### Post by luca5am on 2011-05-24
Have you tried using ctrl+alt+t as a shortcut for opening the terminal (which is, I think, the default shortcut)?

Then run
```
> ccsm
```To run the compiz config manager and change the settings back to a working state.

---

### Post by Grenage on 2011-05-24
> **Arifcatalyst said:**
> I Installed Compiz, to play with some settings in unity!!!

But, ufortunately I ended up in MessUp!!:(

I Clicked On dektop Cube In compiz and ignored all through the way!!!

When I login, I can't access any panel, Cant open Terminal Using Alt+f2...just a dumb cursor and blank desktop!!!

I searched whole through teh forum..but cudnt find teh Appropriate Soln!! :confused:

From a terminal, this should reset the Unity compiz settings:

```
unity --reset
```

If, and only if that does not work, try:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by Arifcatalyst on 2011-05-24
> **Grenage said:**
> From a terminal, this should reset the Unity compiz settings:

```
unity --reset
```If, and only if that does not work, try:

```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

thanxxx!!! Done

But When i login in ubuntu clasic aka gnome2.32...i still get the unity dock

any way To remove that only in ubuntu classic Environment!!

---

### Post by Grenage on 2011-05-24
> **Arifcatalyst said:**
> thanxxx!!! Done

But When i login in ubuntu clasic aka gnome2.32...i still get the unity dock

any way To remove that only in ubuntu classic Environment!!

Make sure that the unity plugin is unticked in the compiz settings. It should unable it when logging in to a unity desktop.

---

