---
title: "What is the name of the applet that notifies you of available updates?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by josephellengar on 2010-01-13
I can't remember what it was called and on my old computer I had it installed, but on this one I don't and I just realized that I was 200+ mb behind in updates.  I thought it was called apt-watch-check or something but no applet by that name is installed.  Does anybody know what I am talking about or have a viable alternative?  Thank you.  (I'm using gnome)

---

### Post by llama320 on 2010-01-13
I think it's just called update-manager, unless I misunderstood what you're asking for. To check if it's installed run 
```
aptitude search update-manager
```
If there's an 'i' a the front of the line, it's installed.
 
Also, a note: We're using the same laptop :)

---

### Post by josephellengar on 2010-01-14
> **llama320 said:**
> I think it's just called update-manager, unless I misunderstood what you're asking for. To check if it's installed run 
```
aptitude search update-manager
```
If there's an 'i' a the front of the line, it's installed.
 
Also, a note: We're using the same laptop :)

I have update-manager, but on my old system there was a gnome-panel applet that told me when there were available updates.  On this system I'm not getting the popup or anything.  A little dangerous, security-wise.

---

### Post by llama320 on 2010-01-14
What about apt-watch-gnome? Is that what you're looking for?

---

### Post by J V on 2010-01-14
> **rossholley said:**
> On this system I'm not getting the popup or anything.  A little dangerous, security-wise.Depends... jaunty got rid of the applet for pupops, I get rid of the popups for the applet :P

gconf-editof apps > update-notifier > autolaunch

if its on, you should get popups... these are really annoying and don't always work...

if its off, you should get the applet, much much nicer...

---

### Post by josephellengar on 2010-01-14
> **llama320 said:**
> What about apt-watch-gnome? Is that what you're looking for?

Exactly what I was looking for.  Thank you!  solved.

---

### Post by cova on 2010-01-14
Looking in the startup applications gui, this is selected in the checklist yet I do not see this displayed in my notification area either. Keep having to manually check myself.
EDIT: Didnt notice the apt-watch-gnome suggestion. Have that now thanks. Is this not set up as default anymore then?

---

