---
title: "Argh having issues installing Remastersys. . .Not Found"
date: 2010-09-03
forum: New to Ubuntu
---

### Post by Fableflame on 2010-09-03
Okay, so I was installing Remastersys, using the instructions I found here:
[http://my-wd-local.wikidot.com/otherapp:how-to-install-remastersys](http://my-wd-local.wikidot.com/otherapp:how-to-install-remastersys)

But when I run 

"sudo apt-get install remastersys"

It tells me

"E: Couldn't find package remastersys"

Help?

---

### Post by inameiname on 2010-09-03
Remastersys isn't in the official Ubuntu repos. You must add it's repo:

[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)


That link you gave is for an old repo for it. Use the one I gave.

---

### Post by spillage2 on 2010-09-03
have you tried to install it from the ubuntu software centre.

---

### Post by inameiname on 2010-09-03
What packages that are inside the Ubuntu Software Center are merely what are in the official Ubuntu repos and perhaps any PPAs and sources already installed. It's mainly just another way to see what packages are in the official repos. Thus, to install Remastersys, you need it's repo to get it, and Ubuntu Software Center won't see it until it's source is added.

---

