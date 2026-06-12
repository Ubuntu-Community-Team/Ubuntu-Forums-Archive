---
title: "Gnome Panel in XFCE"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by spillin_dylan on 2009-05-16
I have installed the XFCE desktop environment (along with a few others; LXDE, Fluxbox, ...) to try it out.  I had it set up fine, but now instead of the default XFCE panels showing up, I am getting my Gnome panels instead.  

What might have changed, and how can I get the XFCE panels back to the way they should be?

---

### Post by guywithcable on 2009-05-16
Can you post a screenshot? Is gnome-panel running?

---

### Post by spillin_dylan on 2009-05-17
Okay, here's a screenshot of each.  I'm positive that is the Gnome panel on both shots, because I had the XFCE panel configured differently.
Gnome:[ATTACH]114175[/ATTACH]    XFCE:[ATTACH]114176[/ATTACH]

---

### Post by guywithcable on 2009-05-18
Yeah, that looks like gnome-panel. Hmm... Is there any .xfce (or something of that nature) in your home folder? It might be in .config, so check there too. If so, what's in it?

---

### Post by kerry_s on 2009-05-18
do you got gnome-panel in your startup?

if not try killing gnome-panel> **killall gnome-panel**
then start xfce4-panel> **press alt+f2**, type> **xfce4-panel**
logout and tick the save session box, then log back in.

---

### Post by spillin_dylan on 2009-05-18
Thanks, kerry, that worked!  I haven't logged out & back in yet to make sure it saves the session, but I checked the box as you said, so I'm sure it will.  

As for the .xfce & .config:  I don't have any .xfce at all, and .config contains two folders xfce4/ and xfce4-session/ which both have mostly XML files in them.

---

### Post by Lampi on 2009-05-18
maybe you need to chose session "xfce" in gdm login manager? Best is you make it your default session choice right away.

---

