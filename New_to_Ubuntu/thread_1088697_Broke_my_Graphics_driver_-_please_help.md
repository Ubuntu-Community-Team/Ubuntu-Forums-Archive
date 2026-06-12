---
title: "Broke my Graphics driver - please help"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by marysiak on 2009-03-06
Everything was going fine (if by fine you mean lots of fiddling and installing things), but while trying to get my dvd drive to play dvd's I have completely broken all the graphics.

On my initial install of Hardy I remember I had to do some fiddling to get the graphics to work, but I don't remember what I had to do.

I am using an ATI Sapphire HD 2400 XT graphics card and have no onboard graphics on the motherboard (asus p5q pro). I have the 64 bit version of Hardy installed.

I went into the Admin: Hardware Drivers and enabled an ATI driver. On restart I got a black screen with a white square. I did some fiddling and managed to get it to boot into failsafe gnome mode with no network connection, but during the process of trying to fix it fully I have ended up back unable to boot even to the login screen, it goes to a blank white screen now. 

But at somepoint during this process it installed the 24 kernel.

So currently on the 24 kernel I can only do things that can be done via the root command line, but I can still get to gnome failsafe using the 23 kernel.

What do I do?

What can I do in failsafe gnome mode with no internet connection via kernel 23?

What can I do via command root with no internet connection via kernel 24?

I can download files via my laptop and transfer them by usb stick.

---

### Post by marysiak on 2009-03-06
Of course the second you post you try something and it mysteriously works. Using failsafe gnome on kernel 23 I edited xorg.conf to add vesa as a driver and now everything is miraculously working - it's even playing dvd's. Well except I have to refix my network connection, the fix for that got overwritten by the new kernel I think.

Anyway, consider issue fixed and topic closed.

---

### Post by cwsnyder on 2009-03-06
If I can read my notes properly, try this at the command root```
$ sudo dpkg -reconfigure -phigh xserver-xorg
```

---

