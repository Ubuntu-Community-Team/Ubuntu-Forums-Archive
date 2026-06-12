---
title: "evolution strange behavior"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-14
i recently changed my login-root password and evolution all of the sudden keeps asking me about all my mail passwords and the default keyring why?

also how to recover the password for default keyring?(i dont even remember setting one!)

---

### Post by Jeff250 on 2009-07-14
When your login password and keyring password are the same (which they are by default), then your keyring will be automatically unlocked when you log in.  Since you changed your login password, your keyring isn't automatically unlocked anymore.  To fix this, do this:

Go to Applications -> Accessories -> Passwords and Encryption Keys (or run seahorse from terminal)
Go to 'Passwords' tab
Right click on 'Passwords: login' keyring and select 'Change Password'
Change the password to match your new login password

This should automatically unlock your keyring the next time you log in.

---

### Post by heyyy on 2009-07-14
well it couldn't be simpler the default keyring was the previous password...
many thanks

---

