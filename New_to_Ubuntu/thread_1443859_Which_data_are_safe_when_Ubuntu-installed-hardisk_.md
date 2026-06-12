---
title: "Which data are safe when Ubuntu-installed-hardisk read on other systems?"
date: 2010-03-31
forum: New to Ubuntu
---

### Post by hyapadi on 2010-03-31
I want to know how safe is the data in default Ubuntu security settings, when somebody got access to physical hardisk.

As far as I know, by default the hardisk is not encrypted. Therefore most of the data can be read easily, except for login password and perhaps other passwords too (firefox, gaim, etc) that encrypted / hashes. Please elaborate more and correct me if I'm wrong.

:popcorn:

---

### Post by NCLI on 2010-03-31
Pretty much. Anything not encrypted will be easy to access. If you don't want this, you can easily encrypt your home folder during setup.

---

### Post by denver on 2010-03-31
Without encryption it does not matter what OS you wrote the data under. Be it windows, linux, Unix or any other OS out there, if no encryption is used, its as easy as mounting the hard drive and copying it.

If you really want to secure your data and you have something ultra super secret (like the secret of why women go to the bathroom in pairs) then encryption is the way to go.

Ubuntu 9.10 has this option at install time.

---

### Post by hyapadi on 2010-04-01
If I didn't turn it on at the installation. How if I want to turn it on later on without re-installation?

Regarding the login password, is it encrypted by default?

How about Gaim? is it encrypted by default? As far as I know it should be protected by gnome-keyring by default. Is it true?

---

### Post by denver on 2010-04-01
You should be able to find some info on the matter [*here*]("https://help.ubuntu.com/community/EncryptedHome") and [*here*]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

Login passwords are all encrypted by default. Pidgin on the other hand stores its passwords in clear text.

Gnome-keyring stores saved passwords and public/private keys and uses them if you allow it to.

---

