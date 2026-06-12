---
title: "Motorola SM56 Modem &amp; ttySL0 permissions"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by mikeincal on 2008-02-18
Hello everybody,

I have just built up two systems with flexibililty in mind. Both of these systems have Motorola SM56 modems installed for the intended end user. These were pulls from my old Windows systems that I won't miss. I have both the ungrab-winmodems and the slamr drivers(?) installed along with gnome-ppp. Surprisingly, the modem works, but only when ran from a terminal as root. As a standard user, the modem is not even detected in gnome-ppp. I have isolated the offending file as ttySL0 in the /dev directory. I have used chown to change the user and to add permissions to each group. This will work until I reboot. After rebooting, the permissions become Root=owner with full read/write, Group uucp has read/write abilities, and other groups have no rights. I do not see the uucp group in the users properties box either.

Does anyone know how to permenantly change the file permissions or add the user to an appropriate group? I would rather not make the user a full time root user, nor do I want to go back to Windows.

Any help is appreciated.

---

