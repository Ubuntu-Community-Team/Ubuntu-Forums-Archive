---
title: "Changed password and now network manager needs to be unlocked"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-04-23
So I changed my user password using passwd command, but now when I log in it tells me the network manager applet needs me to unlock the key ring... which has the old password. How can I fix it so this doesn't come up anymore/uses my new password?

~Jeff

---

### Post by Melk79 on 2009-04-23
Go to Applications>Accessories>Passwords and Encryption Keys

On Intrepid, I think you can change the keyring password under the preferences tab.  On Jaunty, it's under the passwords tab.

---

### Post by Hospadar on 2009-04-23
It's a little confusing, the "keyring" password is separate from your user password, if you want to change it or just remove it so you don't get prompted (which is not technically very secure, but I don't care so much about my wifi passwords so I ususally just leave it blank), you can use seahorse to do so.

first install it, from synaptic or "sudo apt-get install seahorse" then run it, Alt-F2,  "seahorse"
Go to passwords, right click on "default" and "change password"

If you leave the new password blank, it will give you a message about unsafe storage (because the passwords being held in the keyring will not be encrypted) but also you won't get prompted about your keyring password again.

---

