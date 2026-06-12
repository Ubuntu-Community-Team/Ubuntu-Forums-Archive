---
title: "Ubuntu in Windows"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by billyss on 2010-09-29
Hello mates, I just wanted to know a couple of things about installing ubuntu in Windows... Is the only way through Wubi (and of course virtual machines) or is there any other way to actually install ubuntu within windows?

I ask because once I saw a video, where in a windows rocketdock or something there was a button with linux logo (actually the foot logo, more likely gnome) and it was like linux within windows (he was performing some tasks). But I can't remember at all what it was about.

Sorry if that sounds dumb, just wanted to confirm what I saw... perhaps it could be something else... 

Cheers :)

---

### Post by philinux on 2010-09-29
I can't recommend wubi due to grub2 problems that I've seen. VB yes. Or try a persistent live usb stick.

---

### Post by billyss on 2010-09-29
Thank you for the tip Philinux! :)

---

### Post by P4man on 2010-09-29
Agreed about avoiding wubi. But there are other ways to "run linux" on windows. Well, not really linux, but linux apps or even the desktop environment.

First there is cygwin
[http://www.cygwin.com/](http://www.cygwin.com/)

If you just want a unix/linux-like shell.

Secondly, KDE (one of the popular linux desktop interfaces) is actually compiled for windows. I dont know if its a good idea, or how stable and functional it is,  but if you like playing with these kinds of things, here you go:

[http://windows.kde.org/](http://windows.kde.org/)

Last point; virtualbox supports "seamless mode" (at least on a linux host, but I think it will work on windows host too). That lets you run your virtual apps in native windows. Kind a hard to explain, have a look here:
[http://www.youtube.com/watch?v=Kxk6oFqMJVY](http://www.youtube.com/watch?v=Kxk6oFqMJVY)

Although its the opposite, windows VM running seamless inside ubuntu, but the idea is the same.

---

### Post by billyss on 2010-09-29
Thanks a lot, that's what I was searching! :KS

---

### Post by mocoloco on 2010-09-29
It was probably [Portable Ubuntu]("http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows").

Haven't tried it myself but the idea looks cool.

---

### Post by billyss on 2010-09-29
> **mocoloco said:**
> It was probably [Portable Ubuntu]("http://lifehacker.com/5195999/portable-ubuntu-runs-ubuntu-inside-windows").

Haven't tried it myself but the idea looks cool.

 That's exacly what I saw.. I'm going to try it, many thanks mate ;)


EDIT: It doesn't work at x64 version of windows. The best way would be a live CD as it seems...

---

### Post by Mark Phelps on 2010-09-30
If it's any consolation, I tried the 32-bit version, and while it worked, it was awful.  Very S...L...O...W  and lots of display artifacts.  Shudder to think that is folk's first (and probably ONLY) exposure to Ubuntu.

---

