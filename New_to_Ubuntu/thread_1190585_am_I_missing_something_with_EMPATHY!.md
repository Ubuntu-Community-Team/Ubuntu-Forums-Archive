---
title: "am I missing something with EMPATHY!?"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by nakama85 on 2009-06-18
I have downloaded empathy (sudo apt-get install empathy)
I have read many places that it supports voice chat, however I don't see any options to voice chat. What am I missing??

Thanks for any help!

---

### Post by nakama85 on 2009-06-18
+1

---

### Post by glroig on 2009-06-19
deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) jaunty main

---

### Post by shae on 2009-06-19
```
sudo apt-get install telepathy-butterfly telepathy-gabble telepathy-haze telepathy-idle telepathy-salut telepathy-sofiasip
```

This should handle most of the protocols.  I may have missed one or so though.  Look for packages named telepathy-*.

---

### Post by Sef on 2009-06-19
Here is the [PPA Telepathy site]("https://launchpad.net/%7Etelepathy/+archive/ppa").

---

