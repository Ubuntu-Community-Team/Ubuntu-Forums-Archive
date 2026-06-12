---
title: "Wireless network and keyring."
date: 2009-09-02
forum: New to Ubuntu
---

### Post by mvalviar on 2009-09-02
I enabled auto-login for my account. My pc connects to a password protected wireless network. Everytime I auto-login it prompts me for a password to access the default keyring. How do I tell ubuntu to automatically access the keyring and thus automatically connect to the network?

---

### Post by gali98 on 2009-09-02
Which version are you on (Jaunty?)
It should, when it asks for you password, also have a little checkbox that says remeber this authentication (or something like that...)
Kory

---

### Post by sahabcse on 2009-09-02
follow below url for resolving default keyring issue

[http://ubuntulinux.co.in/Default-keyring-can%27t-unlock---Ubuntu-8-10.php](http://ubuntulinux.co.in/Default-keyring-can%27t-unlock---Ubuntu-8-10.php)

---

### Post by mvalviar on 2009-09-02
> **gali98 said:**
> Which version are you on (Jaunty?)
It should, when it asks for you password, also have a little checkbox that says remeber this authentication (or something like that...)
Kory

There isn't any checkbox :(

---

### Post by gali98 on 2009-09-03
Hmmmm....
Okay... Try doing this:
Rightclick on the networkmanager icon and select edit connections.
Then go to the wireless tab and select your network.
Click edit then look in the bottom of that window. There should be a checkbox that says "Available to all users."
Try checking that then see if that helps.
Kory

---

### Post by betterspud on 2009-09-05
Was having the same problem and this has fixed it for me.

Cheers gali98

---

### Post by piperdown10 on 2009-09-05
> **betterspud said:**
> Was having the same problem and this has fixed it for me.

Cheers gali98

Fixed it for me too. :KS

---

### Post by gali98 on 2009-09-07
Sweet! :)
Glad it worked.
Kory

---

