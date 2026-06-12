---
title: "DWL-G650 help"
date: 2007-05-13
forum: Networking &amp; Wireless
---

### Post by jessej on 2007-05-13
Hello everyone,

I have this D-link model wireless card.  I also have Ubuntu Edgy installed as a command line system.  I got this wireless card from a friend and have spent a good amount of the day trying to get it to work.  I have searched the posts here and elsewhere but nothing really clicked.

I know I need to install drivers for it but I don't know where to start.

Any help would be appreciated

Thanks
JesseJ

---

### Post by Co.Sinecure on 2007-05-13
Have you installed the restricted-modules package? That has worked for me with that particular card.

---

### Post by jessej on 2007-05-13
I haven't tried that.  Could you please give me more information about it?

Thanks

---

### Post by Co.Sinecure on 2007-05-13
Using apt-cache, search for something called "linux-restricted-modules-..". You'll need to make sure that the kernel matches what you have installed (the text that comes after '-modules-'. Maybe check what version "linux-modules-..." is, or can you use "uname -a" or something? I can't remember..)
This should install some extra drivers including the one you need!

I just installed feisty on my laptop as a command line install, and it automatically installed the drivers I needed for this card, too easy!

---

### Post by jessej on 2007-06-10
It works now.

I updated Edgy on the laptop to Feisty.  I also then install the restricted modules.
After that i entered:

sudo dhclient

and online i was!

Thanks!

---

