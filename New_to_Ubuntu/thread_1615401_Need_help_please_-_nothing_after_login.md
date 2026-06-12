---
title: "Need help please - nothing after login"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by luckylucky on 2010-11-06
OMG, I really need help to get this one fixed.  Please please please.  I just bought this laptop a few days ago and spent many hours getting Ubuntu 10.10 just perfect.  I really really really don't want to have to do a fresh reinstall.

The problem started by having an external monitor hooked up to the laptop, worked fine, then I tried to change a monitor settings (didn't really do much).  Something weird happened.  I rebooted hoping that would "fix" the problem.

No booting up is ok, but after loging in I am greeting with my desktop, a black un-functioning with no icons panel, with a slight flicker.  Mouse won't even move with touchpad.  Nothing really works.

Rebooted multiple times and nothing.

Tried seeing what I could do by selecting recovery mode from grub.  Tried to fix xorg, and that only resulted in touchpad not working now :(  Did dpkg, nothing.  Even trying to start in failsafe graphics brings me to the same problem.

Idea 1: Maybe from terminal (I can do that) is there a way to reconfigure my monitor settings?

I am open to suggestions.  Thank you in advance for your assistance.

---

### Post by luckylucky on 2010-11-07
update

I (in root) went into my home folder and changed the names of the ".gconf" and ".gconfd" folders.  Upon booting in ubuntu created a new set of folders with the data, and now these things work well... or at least I'll redo some of my own settings.

I still have the problem that I subsequently creating while mucking around trying to fix Xorg, which wasn't broken then, but is now.  My touchpad doesn't work.  Trying now to solve that one somehow.

---

### Post by luckylucky on 2010-11-07
I feel like such a tool.  Fn + F7 did the trick.  I must have pressed it while going for F6 in my desperate attempts to do something useful.

Marking thread as solved. Thanks anyways

---

### Post by tajiknomi on 2010-11-07
*[SIZE=2]thats great. u solved it yourself...[/SIZE]*;)

---

