---
title: "USB printer"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by tony.morse on 2009-08-18
In Ubuntu my HP usb printer is found without any problems, but in Mythbuntu with the Gnome desktop the find printer dialogue seems different and doesn't find the printer. What do I need to install to fix this???

Cheers

---

### Post by XubuRoxMySox on 2009-08-18
Make sure you have CUPS installed (Synaptic). CUPS was just recently updated, too, so if it's already installed, use the "Reload" and then "Mark All Upgrades" buttons to make sure it's up-to-date.

There are also some HP packages in Synaptic that may correspond to your printer. Mark for installation, hit Apply.

Let us know if this doesn't do the trick... I'm not familiar with Mythbuntu at all, but that's how it's done in "vanilla" Ubuntu.

-Robin

---

### Post by tony.morse on 2009-08-19
Hmm, thats not done it, CUPS installed and various HPlips etc... 
It doesn't auto find the printer, but then the options for manual configuration dont seem to include USB, i.e. serial port / parallel port / network.

I thought CUPS was for network printers anyway?

---

### Post by tony.morse on 2009-08-19
FIXED!!!  This wasn't working even after a reboot but the latest update manager resulted in HPlips discovering the printer and all is good now.

Thanks for the help

---

