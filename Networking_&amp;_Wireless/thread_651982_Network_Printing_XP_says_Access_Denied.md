---
title: "Network Printing XP says Access Denied"
date: 2007-12-28
forum: Networking &amp; Wireless
---

### Post by Geffers on 2007-12-28
Previously I had an Epsom printer (Parallel port) connected to my Ubuntu Gustsy box, printed fine on SAMBA network to an XP laptop.

I have now got a HP Photosmart 5280 printer scanner, installed it on my Ubuntu machine using USB, both printer and scanner work fine.

Now if I install it as a network printer on my XP machine it finds it, installs the drivers OK and shows up as an extra printer but the properties box says 'Access denied, unable to connect'.

Totally baffled at the moment, any clues appreciated.

Geffers

---

### Post by ashughes on 2008-04-13
I am having the same problem from a Vista laptop to a USB printer shared from my Ubuntu desktop.  I can print from my Ubuntu laptop.  The only thing I can think of is if there is some permission or group that I need to add my guest user account to.

Any ideas (apart from upgrading Vista to Ubuntu, of course)?

---

### Post by Geffers on 2008-04-13
> **ashughes said:**
> I am having the same problem from a Vista laptop to a USB printer shared from my Ubuntu desktop.  I can print from my Ubuntu laptop.  The only thing I can think of is if there is some permission or group that I need to add my guest user account to.

Any ideas (apart from upgrading Vista to Ubuntu, of course)?

I can't recall how I exactly did it but I assume you have CUPS (Common Unix Print System) running, I then from the XP or Vista machine set up a new printer via the wizard, go for a network printer and the address I used was ipp://ip address of machine hosting printer:631/printers/name of printer

The :631 is the port used by CUPS and ipp printing and the name of the printer appears in your printer manager.

Works fine now.

Geffers

---

### Post by ashughes on 2008-04-13
Thanks for your help, but it still does not work at all under Vista.  Maybe I will just upgrade the laptop to Linux.

---

