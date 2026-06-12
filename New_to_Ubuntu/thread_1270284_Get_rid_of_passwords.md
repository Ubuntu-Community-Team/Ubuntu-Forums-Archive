---
title: "Get rid of passwords?"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by triplesick on 2009-09-19
Hi--

I'm sick of typing in my password when I start up my computer, when I bring it out of sleep mode, to unlock my keyring, etc.  Is it possible to completely do away with passwords, aside from the root password?

Thanks.

(actually, side note.  is it possible to do away with the root password too, and just give myself all possible permissions?  i don't understand how permissions work, so maybe this is impossible.  but i cannot fathom a situation where my i would need to password-protect my computer from anything, or where i would need to restrict permissions on anything, being that i am the only person who uses it.)

---

### Post by snowpine on 2009-09-19
Yes, it is possible... but we are not allowed to discuss it here on the official support forums, as it is really bad security practice. :)

You can enable automatic login from the GDM settings manager (under System->Admin->Login). That will save you from typing your password when you start up at least.

You could also give yourself a really simple password, like '123'.

---

### Post by wojox on 2009-09-19
This should help, but understand sudo not only protects you from others, but also yourself:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by lswb on 2009-09-19
You can enable automatic login so no password is required:

Main Menu/System/Administration/Login Window/Security, then check the box for "Enable automatic login" and fill in your username.

Then disable screen locking when the screensaver kicks in:

Main Menu/System/Preferences/Screensaver and make sure the "Lock screen ,,," box is NOT checked.

The last thing is to set your keyring password to be the same as your login password. Main Menu/Applications/Accessories/Passwords and Encryption keys/Passwords. Right click on "Passwords:login" and select "change password" then set it to be the same as your login password. 

These steps will likely eliminate most of the inconveniences you experience while not changing any system file permissions or otherwise compromising security. And a password will still be required when you want to change something at the admin or root level. Otherwise it would be just a little _too_ easy to accidentally mess something up.

---

