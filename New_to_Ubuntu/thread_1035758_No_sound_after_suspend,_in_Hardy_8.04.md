---
title: "No sound after suspend, in Hardy 8.04"
date: 2009-01-10
forum: New to Ubuntu
---

### Post by swarup on 2009-01-10
This is a problem I tried to solve in the initial months after Hardy came out, but could not get a solution. The sound works fine after I boot up the computer. But if I put it in suspend (which I do all the time), and then try to use the sound, it won't work. Has anyone seen a good solution to this? (I use a Gateway Solo laptop)

---

### Post by taseedorf on 2009-01-12
you'll have to edit  /etc/modprobe.d/alsa-base (assuming you're using alsa)

so...in terminal

sudo gedit /etc/modprobe.d/alsa-base

add this to it
# Reenable Sound after a Suspend
options snd-hda-intel model=gateway

might work?

---

