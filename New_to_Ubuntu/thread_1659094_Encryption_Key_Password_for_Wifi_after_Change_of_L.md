---
title: "Encryption Key Password for Wifi after Change of Login Password?"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by mapes12 on 2011-01-03
Hi

As system admin I have changed the log on password for my of my desktop users but when the user logs in another window pops up saying something about the password not matching the keyring to load the wifi password. I've been all over the system and can't figure out how to correct this. She has to enter the old password to load the wifi settings.

Thanks for any help.

Mark

---

### Post by Vermind on 2011-01-03
The way to fix this is with the keyring gui tool called seahorse.
It is called "passwords and encryption keys" in the menu.
In the tool, you can right-click a keyring and change its password.

The other way is to reset the keyrings, but that means the wifi settings have to be re-entered:
```
rm /home/user/.gnome2/keyrings/*
```

---

### Post by mapes12 on 2011-01-03
Vermind

Thank you!

The Terminal command worked just great.

Mark

---

