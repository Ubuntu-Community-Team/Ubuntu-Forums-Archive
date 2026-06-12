---
title: "Window Won't Drag All The Way To Second Screen"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by UnsafeData on 2009-07-14
Windows don't drag all the way onto my other screen, which is on the right.  The windows get stuck around the left side of the window, and I can't drag it any further. Here's a pastebin of xorg    [http://pastebin.com/dddaed41](http://pastebin.com/dddaed41)

I have the ATI HD4670, and I'm using the radeonhd drivers..

---

### Post by Paddy Landau on 2009-07-14
Are you sure that the computer knows it's on the right side? Have you tried dragging to the left, or up, or down?

Have you told the computer that there are two screens and you want to use them as dual-screen?

---

### Post by UnsafeData on 2009-07-14
> **Paddy Landau said:**
> Are you sure that the computer knows it's on the right side? Have you tried dragging to the left, or up, or down?

Have you told the computer that there are two screens and you want to use them as dual-screen?

I went into display settings, changed the refresh rates of both monitors to 75Hz, and windows drag fine now. I changed one monitor back to 85Hz and it still works.

Am I doing it right nevertheless? Also how do I take a screenshot of just one screen

---

### Post by UnsafeData on 2009-07-14
I can't take a screenshot of both monitors, or just one monitor. I downloaded scrot and it's still the same.

---

### Post by UnsafeData on 2009-07-14
** "scrot -m" works, thing is I have to put both screenshots of both **halves together, and that isn't fun

---

### Post by UnsafeData on 2009-07-14
Actually scrot -m doesn't seem to work.. Scrot -s is the one that takes the screenshot of my other monitor, but then I have to select it perfectly though..

EDIT: scrot -s doesn't work either, my bad..

---

### Post by Paddy Landau on 2009-07-15
The standard way of taking a screenshot in both Ubuntu and Windows is by pressing the Print Screen button.

When you press Alt-Print Screen, it captures just the current window.

When I press Print Screen, it captures the entirety of my workspace, i.e. both monitors together.

Edit: Some keyboards show Print Screen as an abbreviation, such as PrtSc.

---

