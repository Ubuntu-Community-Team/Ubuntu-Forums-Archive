---
title: "Best way to add kubuntu-desktop to my ubuntu installation"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by CLVPX on 2008-12-10
I read on another forum that I am better off using
```

sudo aptitude install kubuntu-desktop
```

than using

```
sudo apt-get install kubuntu-desktop
```

for removing purposes, as it is a metapackage, apparently apt-get remove does not remove it completely.

What would be the best (and safest) way to install it, so that I can safely revert to my current system state?

---

### Post by theozzlives on 2008-12-10
```
sudo apt-get install kubuntu-kde4-desktop
```

FYI: on your signature, 8.04 is Hardy...8.10 is Intrepid

---

### Post by CLVPX on 2008-12-10
Haha, my bad, I must've only changed the number when I upgraded.

And if I want to uninstall will my system be back to where it was? When I did this on 8.04 it left a lot of the additional packages which I had to manually remove.

---

### Post by taurus on 2008-12-10
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by Bölvaður on 2008-12-10
You will be able to pick either GNOME or KDE from login screen... well that is what I have seen, highly unlikely it is different on ubuntu.

you can also install via synatpic package manager, but I guess the fastest way is always the terminal... with few exeptions.

---

