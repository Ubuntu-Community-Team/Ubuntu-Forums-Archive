---
title: "Top Bar has Disappeared"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by warfare on 2011-03-23
haven't used this program very much.  it is on my mini laptop.  i somehow messed up my top bar on desktop.  the place where you find all your programs,log out,ect.  don't know how to get it back.  i changed the appearance hoping it would pop back up there, but of course not.  anyone...HELP

---

### Post by Sef on 2011-03-23
Moved to ABT.

---

### Post by matt_symes on 2011-03-23
Hi

> haven't used this program very much. it is on my mini laptop. i somehow messed up my top bar on desktop. the place where you find all your programs,log out,ect. don't know how to get it back. i changed the appearance hoping it would pop back up there, but of course not. anyone...HELP

Can you post a screen shot ?

Kind regards

---

### Post by Krytarik on 2011-03-23
> **matt_symes said:**
> 
Can you post a screen shot ?

LOL:D  Of what, nothing?!

If you are fine with simply resetting all your panels, run this command in a terminal:
```
gconftool-2 --recursive-unset /apps/panel && killall gnome-panel
```If you think you may have just set it to "autohide", run this instead:
```
gconftool-2 /apps/panel/toplevels/top_panel_screen0/auto_hide -t bool -s false
```Greetings.

---

### Post by matt_symes on 2011-03-23
Hi

> LOL Of what, nothing?!

Yes, if necessary. 

Reason... To check to see exactly what is going on. Less mistakes happen that way.

Kind regards

---

