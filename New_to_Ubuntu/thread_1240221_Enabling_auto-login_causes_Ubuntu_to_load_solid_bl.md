---
title: "Enabling auto-login causes Ubuntu to load solid black with just the mouse cursor."
date: 2009-08-14
forum: New to Ubuntu
---

### Post by diablo75 on 2009-08-14
I just bought a new laptop for my girlfriend and have installed 9.04 on it, with all the most recent updates applied and in effect.  The system has been restarted several times so all seems to be working well.  Except if I enable auto-login via System>Admin>Login Window>Security tab.  Doing this causes Ubuntu to begin to login, but it seems to snag and just sit there at a solid black background with the cursor.  I was able to reverse this by editing the /etc/gdm/gdm.conf-custom file, changing the automaticlogin value to false.

So I don't really need help getting the system back to the way it was but I'd really like to know if there's a fix for this issue so I can re-enable automatic login.

---

