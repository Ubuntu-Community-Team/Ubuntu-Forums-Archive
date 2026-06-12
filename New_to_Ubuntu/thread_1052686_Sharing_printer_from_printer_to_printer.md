---
title: "Sharing printer from printer to printer"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by diablo75 on 2009-01-28
Fresh install on my girlfriends computer.  Just attached a HP laserjet 6P via LPT port.  I think it's sharing... but not very sure how to be certain about that.  Assuming that it is, what do I look for on my PC to add it so I can print to it?

---

### Post by Peter09 on 2009-01-28
On your machine, in a browser type the address

[http://localhost:631](http://localhost:631)

this will bring up the CUPS printer interface. 

In Administration use the search for printers utility to find your shared printer.

---

### Post by diablo75 on 2009-01-28
It says no printers found... so I guess I've not properly shared it.  How do I do that?

---

### Post by Peter09 on 2009-01-28
Use the same program on your girlfriends machine to share the printer.

---

### Post by boof1988 on 2009-01-28
> **diablo75 said:**
> Fresh install on my girlfriends computer.  Just attached a HP laserjet 6P via LPT port.  I think it's sharing... but not very sure how to be certain about that.  Assuming that it is, what do I look for on my PC to add it so I can print to it?

I have done it by using the GUI:

System >> Administration >> Printing

And then checking the appropriate boxes.

Attached are the screen shots for the U.8.04 and U.810 Printing menus in the hopes that it helps a little bit.  I am note really sure what each of the options does.  So I can't advise which options to check.  But once I found these options, it made sharing printers a lot easier for me.

EDIT:
Options need to be selected on both machines for it to work (I believe).

---

