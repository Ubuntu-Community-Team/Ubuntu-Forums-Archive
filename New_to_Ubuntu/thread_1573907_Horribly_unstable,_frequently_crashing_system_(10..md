---
title: "Horribly unstable, frequently crashing system (10.04)"
date: 2010-09-13
forum: New to Ubuntu
---

### Post by Montserrat on 2010-09-13
Help. It started with a jumping cursor and randomly selecting text in e-mail and spreadsheets. Actually, it happens with scratch pad, as well as mouse. Using the arrow keys sometimes gets me out of it, but the eventual outcome is a total freeze. When it freezes in the word processor, I lose the content. 

This isn't acceptable. Help.

---

### Post by beew on 2010-09-13
What is your graphic card?

---

### Post by Montserrat on 2010-09-13
Beew,

Thank you very much for the reply. Here's some technical background.

It's a dual install of 10.04 and Win7 on a new Toshiba L505 laptop with a Pentium processor (64-bit OS for both). This system features a 4500 MHD graphics media accelerator incorporated on the motherboard. 

I sure hope I don't have a compatibility issue. I have too much time and effort invested in this configuration, and I can't upgrade the graphics card.

---

### Post by jtarin on 2010-09-13
While I don't have the same setup as you...I did have the same problems with my first installation of 10.04.....very erratic mouse behavior, menus opening and closing usually a right-click got me out of it. It's not a hardware issue I have seen too many reports on this to put it off on just hardware.I finally minimized my problem by backing up with Paragon Partition Manager and then restoring from that image rather than Live CD.I've done this twice and each time it has lessened. I know it sounds a little crazy, but it worked for me.

---

### Post by Montserrat on 2010-09-13
Thanks jtarin. Though I back up religiously, I'm still looking for remedial measures. If I can't get a real fix, could someone tell me about a more graceful way of recovering? Holding down the power button to shut down isn't healthy for the file system. How do I enable the magic sysrq key? And how do I recover the file I was working on when the system crashes?

Help!

---

### Post by jtarin on 2010-09-13
> **Montserrat said:**
> Thanks jtarin. Though I back up religiously, I'm still looking for remedial measures. If I can't get a real fix, could someone tell me about a more graceful way of recovering? Holding down the power button to shut down isn't healthy for the file system. How do I enable the magic sysrq key? And how do I recover the file I was working on when the system crashes?

Help!
[URL="http://library.gnome.org/users/user-guide/2.29/windows-focus.html.en"]You might try Window Focus
[/URL]. As for recovery of an item in a word processor you would have to investigate that word processors properties for that. Example Open Office:  Find backups. If you've checked the "Always create backups" in the OpenOffice settings, OpenOffice.org keeps backups of all your files. You will have to see where the default is or set one. You can also look in your /var/tmp directory possibly.

---

### Post by jtarin on 2010-09-13
[backup: backup files if you've activated the feature in Tools>Options>Load/Save>General, Always create a backup copy.]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=74&t=12426")

---

