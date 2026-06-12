---
title: "[SOLVED] Maybe I'm doing something wrong??"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by fishman78 on 2008-12-23
Hi All,

    I am trying to install 8.10 64 bit on my new MOBO (last one bit the dust)  I have an Asus M3N78-VM board with onboard Nvidia 8200 graphics.  My problem is when I try and install ubuntu 8.10 64 bit or 32 bit or 8.04 32 bit it always goes to a command prompt.  I never get the gui that i've seen before.  Is this video not supported by ubuntu?  maybe I'm doing something else wrong?  All help is appreciated.  Thanks!!

fishman78

---

### Post by taurus on 2008-12-23
How fast did you burn the ISO image?  Did you check the cd for defects at the initial menu?

---

### Post by nerdking on 2008-12-23
very possible it might be the video card, i would contact the manufacturer to make sure.

---

### Post by namdung on 2008-12-23
Are u able to run through live cd?

---

### Post by eagle416 on 2008-12-23
Perhaps you installed the server edition rather than the desktop edition? The server edition doesn't have a GUI.

---

### Post by fishman78 on 2008-12-23
I don't really know how fast it burnt, but I did the CD Integrity check it came back OK.  The Live CD doesn't work either.....straight to the command prompt.  It sounds to me like the graphics card is not supported for install.  Here is the funny thing, I have an image of a previous install that works, at least graphically with this omb card.  This only happens on a clean install/boot.  I'm stumpped.


edit:  It wasn't the server edition, and I downloaded new images just incase, I thought that to at first.  LOL

---

### Post by mkvnmtr on 2008-12-23
At the command prompt you might type startx.

---

### Post by fishman78 on 2008-12-23
> **mkvnmtr said:**
> At the command prompt you might type startx.

And that does.......???

Sorry, I'm new to this.  Windows usually only broke after install! LOL

---

### Post by eagle416 on 2008-12-23
x starts the X window system - the system that the GUI is built on. If you have a GUI, startx tells it to begin.

---

### Post by fishman78 on 2008-12-23
> **eagle416 said:**
> x starts the X window system - the system that the GUI is built on. If you have a GUI, startx tells it to begin.

Sweet!  I'll give er a try!  Thanks, I'll let you know how I make out.

---

### Post by Duck2006 on 2008-12-23
> **fishman78 said:**
> Sweet!  I'll give er a try!  Thanks, I'll let you know how I make out.

If that does not work you may have to do a text base install and config the video after install.
One thing first.
Did you try safe graphic mode?

---

### Post by fishman78 on 2008-12-23
> **Duck2006 said:**
> If that does not work you may have to do a text base install and config the video after install.
One thing first.
Did you try safe graphic mode?


I beleive I did.  And if I remember correctly it came up with a screen asking if I wanted to change the config file, or run a log.  Somthing to that note anyway.  I have no idea how to install ubuntu from the command line.

---

### Post by Duck2006 on 2008-12-23
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by fishman78 on 2008-12-29
Well, I hijacked a 7300 GPU from a friend and it installed fine.  I guess 8.10 doesn't like the 8200 OMB GPU.  After install I installed the nVidia drivers and pulled the card out.  Ubuntu runs fines now with the OMB.  However the startup screen is text and not the fancy Knight Rider progress bar, but i guess that's cause the driver hasn't loaded yet.  Everything else runs and looks great after that!  Thanks for all the help!

Fishman78

---

### Post by taurus on 2008-12-29
Look in /boot/grub/menu.lst to see what the line for kernel says at the end.  Does it say something like **quiet splash**?

Applications -> Accessories -> Terminal
```
cat /boot/grub/menu.lst
```

---

### Post by fishman78 on 2008-12-30
> **taurus said:**
> Look in /boot/grub/menu.lst to see what the line for kernel says at the end.  Does it say something like **quiet splash**?

Applications -> Accessories -> Terminal
```
cat /boot/grub/menu.lst
```

It does list "quite" at the end of each entry.  Is this something I can just delete?  Thanks!

---

