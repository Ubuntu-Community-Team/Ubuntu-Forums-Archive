---
title: "disable Virtual consoles?"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by arikshtiv on 2009-07-31
How can I disable some of the Virtual consoles?

I am using my ubuntu 9.04 for desktop use so I don't need more than one(for a case I'll might need it).

Thanks

---

### Post by kukibird1 on 2009-07-31
> **arikshtiv said:**
> How can I disable some of the Virtual consoles?

I am using my ubuntu 9.04 for desktop use so I don't need more than one(for a case I'll might need it).

Thanks

You can disable them by putting a  # before the start lines in the files 
tty6 tty5 tty4 tty3 in the /etc/event.d  directory.

---

### Post by niteshifter on 2009-08-01
Hi,

Just curious here: Why kill off the virtual consoles? Killing off 5 of the 6 will save about 2.5MB of RAM.

I mean, live like you wanna live and all, but those extra VC can be a handy thing at times.

---

### Post by arikshtiv on 2009-08-01
I want to disable those to save RAM, because this computer has 512MB RAM, but with a very bad hard drive, which can die anytime, so I am trying for ubuntu to use as less swap.

And they will never be useful to me, because I am not an expert or even an advanced user.

And if you hav any more tips to reduce swap usage(eg. free more memory), please tell me, thanks.

---

### Post by niteshifter on 2009-08-01
Hi,

Ok, some memory reduction tips:

Consider using Xubuntu (package xubuntu-desktop). It's window manager (Xcfe) isn't as demanding. It and GNOME (Ubuntu) can coexist peacefully on the same machine, you'll be given an option as to which environment to use at login. 

Use a different browser. FireFox is a heavy user of RAM. The smallest RAM footprint browser is Lynx - but it is console mode, no graphics. Dillo is another lightweight, has a GUI, but IIRC needs a plugin to handle SSL (secure browsing, aka shopping). 

Use OpenOffice much? AbiWord and Gnumeric aren't as RAM hungry as Writer and Calc and are compatible with OOo's file format.

Open System -> Administration -> Services and go through the list. There's probably a few things loaded that you're not using.

---

