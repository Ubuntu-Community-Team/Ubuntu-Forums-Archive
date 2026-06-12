---
title: "access anonymous XP share from Ubuntu"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by irishale on 2007-05-06
Hi... my wife's pc has a shared folder that is shared to anonymous logon user... I can, via Nautilus, browse to her pc, and see the share in the window, however, whenever I try to browse the share, it asks for a username/domain/password.  I've tried all combinations of blank/not blank, anonymous/<the domain>/no password... nothing works... keep getting the password window again.  Call me crazy, but shouldn't anonymous logon mean exactly that... shouldn't 'nothing' work?  How can I get this to work without setting up a user on the windows box?  I had no problem setting up an anonymous share on the ubuntu box that doesn't require login from the XP box, surely there's a way to do the reverse!!!

---

### Post by spd106 on 2007-05-07
Which version of Ubuntu are you using?

Try opening nautilus then press Ctrl+L to get an address bar, then enter this
```
smb://hostname/
```
where hostname = name of your windows PC.

It shouldn't need a password.

On older versions you sometimes had to add the user to the smbusers group. This is done by opening a terminal and entering this command.
```
smbpasswd -a username
```

---

