---
title: "Adding an deb-src line in sources.list"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by Shnooky on 2009-01-04
I'm using a walkthrough forum for installing madwifi drivers on an eeepc with an atheros wireless card and part of the forum is telling me to do this "Ensure you have a deb-src line for restricted in /etc/apt/sources.list first."

Plz help, I am some what familiar with ubuntu but I have no idea were to begin with this one.

-shnooky

---

### Post by taurus on 2009-01-04
You need to edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and remove the # sign in front of all the lines that start with **deb** & **deb-src**.
Save it and close down gedit editing window.

---

### Post by jimmy the saint on 2009-01-04
It is telling you to make sure that you have the restricted repository activated.  Just look at the file and make sure there is no hash (#) in front of the line that includes "restricted"

---

### Post by Shnooky on 2009-01-04
k thx...heres the forum I am using incase anyone is curious, [http://somethingemporium.com/2007/12/the-real-way-to-install-the-new-madwifi-driver-for-the-eee-pc-build-cd-source](http://somethingemporium.com/2007/12/the-real-way-to-install-the-new-madwifi-driver-for-the-eee-pc-build-cd-source)

---

