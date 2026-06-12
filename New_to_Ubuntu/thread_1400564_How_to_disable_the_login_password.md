---
title: "How to disable the login password?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by Yanno on 2010-02-07
Hi,I guess the login passwd quite troublesome so I wanna disable it.Then System->Administration->Users and Groups...Choose the tag 'Properties',just to find the line "don't ask for passwd on login" in faded font,so I can't change it here.Anybody help me out?Thx!

---

### Post by BugBuster on 2010-02-07
Check out System->Administration->Login Screen

Press unlock, type in the admin password and select the user that you want to auto login.

All this assuming you are on Ubuntu 9.10...as mentioned in your avatar.

---

### Post by Isyaltut on 2010-02-07
Have you unlock it yet? Because changing the login screen needs the administrator privilege thus you must enter administrator password. It's right there at System-Administration-Users and Groups. You should see the key icon there at the bottom next to help.

---

### Post by kidux on 2010-02-07
Having your machine auto-login is discouraged because it's supposed to be the first line of defense against security intrusions...

---

### Post by walt.smith1960 on 2010-02-07
> **kidux said:**
> Having your machine auto-login is discouraged because it's supposed to be the first line of defense against security intrusions...

Does having a login protect against online security intrusions, or local? I certainly see the need to protect against unauthorized local access in a public or office setting.  If having a password protected account protects against remote penetration it makes sense to have a password. If password protection only guards against local unauthorized access,  my puddy  cats don't really CARE about what's on my computer unless it controlled a kitty-munch  dispenser:)

---

### Post by 3rdalbum on 2010-02-07
Logging in will also unlock your keyring which stores your wireless encryption key. Setting autologin means that you will need to enter your password to unlock the keyring when you want to connect to wireless.

Yoy might as well just log in manually.

---

### Post by NCLI on 2010-02-07
> **3rdalbum said:**
> Logging in will also unlock your keyring which stores your wireless encryption key. Setting autologin means that you will need to enter your password to unlock the keyring when you want to connect to wireless.

Yoy might as well just log in manually.

If he needs to connect to an encrypted wireless network that is. Otherwise it doesn't matter.

---

