---
title: "txz Touch.. turn it off off off"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-08-28
```
    Option        "Touch"        "on"
```i believe this is the code for touchscreen to be "on" but how do i get to this  so i can turn it "off"

---

### Post by Ayuthia on 2009-08-28
> **R3fr4cti0n said:**
> ```
    Option        "Touch"        "on"
```i believe this is the code for touchscreen to be "on" but how do i get to this  so i can turn it "off"

If you want to be able to turn it on and off you can do the following (from the Terminal--not in xorg.conf):
```
xsetwacom set touch touch off
xsetwacom set touch touch on
```

---

### Post by R3fr4cti0n on 2009-08-28
is there any way to bind a key combo to turn this off n on?

---

### Post by natravis on 2009-08-28
> **R3fr4cti0n said:**
> is there any way to bind a key combo to turn this off n on?

I found [HTML]http://blog.ubrio.us/nix/custom-global-keybindings-in-gnome-ubuntu/[/HTML] 
pretty quickly. Seems to be very straightforward on how to edit global keybindings. I would think you could just set the command to execute a shell script that checks whether Touch is currently on or not, and flips it to the opposite state. Someone else will have to weigh in on how to do that or you could google it. A little googling and experimenting will get you a longgggg way.

---

