---
title: "Package manager broken"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by Dbugger on 2008-12-19
Hi guys. I tried to install second-life from a package of get-deb web and it got stuck so I had to restart the X and now the package manager only allows me to do something called a partial upgrade.

How can I fix this? Thank you!

---

### Post by Michael.Godawski on 2008-12-19
hi,

can you attach a screen shot of the error message?
Applications > Accessories > Take screenshot 

Have you tried to fix this with these terminal commands?

```
sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by tomtom1982 on 2008-12-19
Did you try

```
sudo dpkg --configure -a
```

?

Edit:
Oops. To late. I've to learn type faster;-D

---

