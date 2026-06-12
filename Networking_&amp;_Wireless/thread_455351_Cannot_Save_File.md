---
title: "Cannot Save File"
date: 2007-05-26
forum: Networking &amp; Wireless
---

### Post by johnfarrow on 2007-05-26
I have Thinkpad where the wireless doesn't work.  I attempt to edit and the save the file  etc/network/interfaces.  I use gedit and after I make the changes,  it says "Permission denied"

How can I edit and then save the new information?

---

### Post by lluisanunez on 2007-05-26
```
gksudo gedit /etc/network/interfaces
```

---

### Post by johnfarrow on 2007-05-26
When I enter that I get...

WARNING **: While connecting to session manager:
Authentation rejected, reason : None of the Authentation proocols specified are supported and not based authentation failed.

Any other suggestions, Please?

---

### Post by lluisanunez on 2007-05-26
Yes, you get this error message, but gedit does open, and you can edit the file with admin rights, can you?
Ignore the message and edit away

---

### Post by johnfarrow on 2007-05-26
Yes that worked.  I learned something thanks to you.

---

### Post by lluisanunez on 2007-05-26
Putting sudo before a CLI command (and entering your password) gets you admin rights for this command.
Before GUI commands (such as gedit, nautilus or firefox) it is safer to put gksudo instead of sudo. The only thing is gksudo has this error message bug, but it works all right
Happy to be of help :-)

---

