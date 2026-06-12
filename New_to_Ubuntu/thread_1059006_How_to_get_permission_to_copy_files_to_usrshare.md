---
title: "How to get permission to copy files to /usr/share/"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by maxvenus on 2009-02-03
hey guys, just wanting to get some new skins for my AMSN but im having trouble copying them into the directory specified, i get a permission issue and they just wont copy over! 

Cheers!

---

### Post by binbash on 2009-02-03
add sudo infront of your copy command OR

gksudo nautilus

then copy paste via browser

---

### Post by tomtom1982 on 2009-02-03
Open a terminal and type in

```
gksudo nautilus
```

After this, nautilus is starting in root-modus.

---

### Post by taurus on 2009-02-03
Here's something for you to look over.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by maxvenus on 2009-02-03
thanks guys ! working fine ;)

---

