---
title: "autharity key for sources"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by dvdljns on 2009-09-20
If you add third party sources with gnome loaded there is a panel for adding the auth. key, but I removed ubuntu desktop and all things gnome.
So where do I add that key?

---

### Post by philinux on 2009-09-20
You can do it via terminal. Which source did you add?

---

### Post by dvdljns on 2009-09-20
> **philinux said:**
> You can do it via terminal. Which source did you add?

here is the link.
[https://launchpad.net/~cherokee-webserver/+archive/ppa](https://launchpad.net/~cherokee-webserver/+archive/ppa) 
I need it for 8.04 gutsy

---

### Post by sisco311 on 2009-09-20
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EBA7BD49
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

---

