---
title: "Cd/DVD Reader/Writer issues"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Shpega on 2009-02-14
Okay I can't burn a cd or dvd, I have two seperate burners, now that is one problem, I cannot also read a legit cd from either drive, I can read cd's with mp3's on them, but can't play a normal audio disc.  I can't burn image files or plain data.  any help?

---

### Post by khelben1979 on 2009-02-14
```
sudo apt-get install k3b
```

will install the required packages for cd/dvd burning. Also, some types of discs is not possible to burn with Ubuntu from what I have read on this Ubuntu forum today. Using Verbatim discs should work.

```
addgroup <user> audio
``` might fix your problem with reading audio discs.

When you install different multimedia applications they often choose to install necessary components and might be a good suggestion, I think.

---

