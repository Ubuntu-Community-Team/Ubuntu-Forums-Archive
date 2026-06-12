---
title: "[SOLVED] Mp3's don't work"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by som1special2 on 2008-12-05
just installed and mp3's don't play in rythymbox. It states that supported codec must be found.

---

### Post by Paqman on 2008-12-05
It should pop up and allow you to install the codecs you need.

Scattergun approach: install ubuntu-restricted-extras, which will give you mp3 and multimedia codecs as well as Flash, Java, MS fonts, etc. Always a really good package to install on a fresh machine.

---

### Post by Valtiel on 2008-12-05
> **som1special2 said:**
> just installed and mp3's don't play in rythymbox. It states that supported codec must be found.

That is odd. The first time you play an unsupported file like a .mp3 the software will tell that the file is unsupported and that it will proceed to try to find available codecs.

---

### Post by som1special2 on 2008-12-05
how do i do this? in detail... thanks

---

### Post by nandemonai on 2008-12-05
> **som1special2 said:**
> how do i do this? in detail... thanks

Open up a terminal (Applications -> Accessories -> Terminal) then type:

```
sudo apt-get install ubuntu-restricted-extras
```

After that you should be good to go.

---

### Post by crjackson on 2008-12-05
> **nandemonai said:**
> open up a terminal (applications -> accessories -> terminal) then type:

```
sudo apt-get install ubuntu-restricted-extras
```

after that you should be good to go.

+1

---

