---
title: "Getting rid of Keyring password on startup"
date: 2011-01-27
forum: New to Ubuntu
---

### Post by felipumz on 2011-01-27
Hello,
  I'm a beginner on Ubuntu.  My question is, on startup I get a prompt to enter my keyring password, and it always asks me twice for some reason.  How do I get rid of this?  Please use noob speak, I'm still a noob on Linux.  Thanks!

---

### Post by felipumz on 2011-01-27
By the way I'm using 10.10, I don't know if that would help.  Thanks again!

---

### Post by mal on 2011-01-27
felipumz,

If you have your system set up to log you in automatically, it will need your password to unlock the keyring.  You can check this by selecting the System menu, Administration , Login Screen.  If you change this to require a login password, you should not be asked again to unlock the keyring.

I understand this might not help much, because you will still have to enter a password.

Mal

---

### Post by towheedm on 2011-01-27
I have 10.10 set to auto login and it does not ask for the keyring password.

This happened to me once after changing my account password from the command line.  To reset the keyring password, have a look at:

[http://ubuntu-tutorials.com/2010/01/16/reset-gnome-keyring-password-on-ubuntu/](http://ubuntu-tutorials.com/2010/01/16/reset-gnome-keyring-password-on-ubuntu/)

Hope it helps.

---

