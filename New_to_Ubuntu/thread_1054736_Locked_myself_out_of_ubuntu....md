---
title: "Locked myself out of ubuntu..."
date: 2009-01-30
forum: New to Ubuntu
---

### Post by GrooveTherapy on 2009-01-30
Alright, so in my infinite wisdom, during install of 8.10, I made my account automatically log in.  I didn't like this, so I tried to disable it from System->Administrator.  However, I think I just removed my autologin information because when the login screen appears a "Authentication Failed" prompt appear infinitely, so I can not enter my username and password to fix the settings.

So I'm not about to give up hope...I can enter console mode with ctrl alt f1 and log in there.  However, I'm not sure how to change system administrator preferences or disable the login prompt from the terminal.  Any pointers for this self inflicted epic-level fail?

Edit: Fixed it.  Go to console, edit /etc/gdm/gdm.conf-custom, enabled automatic and timed login

---

