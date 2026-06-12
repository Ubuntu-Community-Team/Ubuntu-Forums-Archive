---
title: "encrypt"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Satendra.kohli on 2009-12-05
How to use encrypt in ubuntu 9.10. is there any guide..

---

### Post by 3rdalbum on 2009-12-05
Encrypt what?

For single-file encryption, I use Bcrypt. It's a command-line program. Install it from Synaptic, run it on the command line (for instance, "bcrypt cool_video.avi").

For full home directory encryption, the Ubuntu installer can do this for you but only on a new install of Ubuntu and a new home directory. At one stage in the install it asks you if you want to Automatically Login, Require a Password to Login, or Require a Password to Login and Decrypt Home Directory. Choose the third one and you're away.

---

