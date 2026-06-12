---
title: "Ubuntu Terminal"
date: 2008-06-23
forum: Networking &amp; Wireless
---

### Post by Rollaj on 2008-06-23
I would like to recycle some old machines we have here at work into terminals.
What I need to do is have a default login to a screen that has a couple of different RDP (windows terminal server) shortcuts.

I don't want the user to be able to do anything other than use those shortcuts. 

Is there a FAQ or has someone that has done this and posted their methods?

Thanks

Tony

---

### Post by forger on 2008-06-23
> **Rollaj said:**
> 
I don't want the user to be able to do anything other than use those shortcuts. 

Are you looking for an internet cafe-like lockdown editor?

> Package: pessulus
Description: lockdown editor for GNOME
 pessulus enables the system administrator to set mandatory settings in
 GConf, which apply to all users, restricting what they can do, which may
 be of particular usefulness for kiosks (internet cafes, for example).
 .
 Examples of what can be locked down are the panels (no changes in the panel
 configuration are allowed, locking their position and their contents), some
 of their functions individually (disabling screen locking and log out), the
 web browser (disabling specific protocols, arbitrary URLs, forcing the user
 to be in fullscreen mode), among many others.

applications > add/remove > search for: pessulus

---

### Post by Rollaj on 2008-06-23
I didn't expect an answer that simple so fast... :)
Yes, it looks like that is exactly what I am looking for.

Thank you

Tony

---

### Post by forger on 2008-06-23
that's the joy of a forum ;)

---

### Post by Rollaj on 2008-06-23
Any other ideas?
I get this error:

Lockdown editor cannot be installed on your computer type (i386).
Either the application requires special hardware features or the vendor decided to not support your computer type.

Computer is a Dell SX260

---

