---
title: "Startup applications - how to &quot;forget&quot; running applications?"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by MoeDrippins on 2009-11-16
9.10:

I mis-clicked (or couldn't help myself) the System -> Preferenceces -> "Startup Applications" -> Options -> "Remember currently running applications".

How can I make Ubuntu FORGET these?  I really don't need them starting every time I log in.

Thanks

---

### Post by Jon Monreal on 2009-11-16
> **MoeDrippins said:**
> 9.10:

I mis-clicked (or couldn't help myself) the System -> Preferenceces -> "Startup Applications" -> Options -> "Remember currently running applications".

How can I make Ubuntu FORGET these?  I really don't need them starting every time I log in.

Thanks

Can't you simply remove them from the list in the "Startup Programs" tab? I apologize, I've never used that feature before.

---

### Post by benj1 on 2009-11-16
or just close all your apps and repeat System -> Preferenceces -> "Startup Applications" -> Options -> "Remember currently running applications".

---

### Post by Arash18k on 2009-12-15
goto
/home/arash/.config/gnome-session/saved-session
and delete everything you dont need to start, or simply you can delete saved-session if you dont want any of them

---

### Post by cyberwiz on 2010-01-18
Thanks for the hint, Arash. Works well for those of us who have pressed that button :D

---

### Post by midtown on 2010-08-25
> **Arash18k said:**
> goto
/home/arash/.config/gnome-session/saved-session
and delete everything you dont need to start, or simply you can delete saved-session if you dont want any of them

Thanks indeed, that's perfect! I feel like it is a gnome bug though, it shouldn't restore the saved session if you don't have that box checked.

---

