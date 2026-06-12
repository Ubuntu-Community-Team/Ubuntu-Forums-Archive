---
title: "Nothing automounts, usb not detected"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by abooks on 2009-11-11
I downloaded Kubuntu 9.10 and have many probs, but this is the worst. I didn't do bittorrent, so it took maybe 8 hours. . .could it have damage? Next question: if I'm always going to have this much trouble with Kubuntu, what do I have to do to revert to good ol' Ubuntu?

---

### Post by eagle416 on 2009-11-11
you might want to check the disk for errors.

```
sudo apt-get install ubuntu-desktop
sudo apt-get remove kubuntu-desktop
```

should revert you back to normal ubuntu.

and what's this about no automounting?

---

### Post by abooks on 2009-11-11
Always prior to loading Kubuntu 9.04, I'd put in a new USB drive, Camera, or CD and up would pop a window and ask me what I wanted to do with it. It would also appear on the desktoop, Id right click and it would tell me to safely unmount. Now nothing like that happens: Amarok detects the CDs but thinks they're empty. I can't find any trace of thumb drives when I put them in. I thought maybe this was just a new Kubuntu thing, but there are so many like that I wonder.

By the way, I didn't make a disk, I just downloaded it. Did I do bad?

---

### Post by abooks on 2009-11-14
After installing Ubuntu and removing kubuntu I got this message

A display manager is a program that provides graphical login
capabilities for the X window system
Only one display manager can manage a given X server, but multiple
display managers are installed.
Please select which display manager should run by default.


There's a little "OK" symbol at the bottom that doesn't do anything. Can I fix this manually?

---

