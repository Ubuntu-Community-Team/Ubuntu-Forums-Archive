---
title: "How to back up my ubuntu files??"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by itsvan on 2009-01-27
im running of the ubunut live disc,,and want to backup all my files,,what can i do? some files i cant open because of a user restriction...i also heard i could also prompt as root from the recovery option and put in some codes,but every time i try to it says i need some password, what can ido?

---

### Post by stoogiebuncho on 2009-02-01
If you're having trouble with user restrictions, you could try running Nautilus (the file manager) as root.

Keep in mind that this can be dangerous if you accidentally delete the wrong file, but since you're talking about running the live CD and booting into recovery mode, I'm guessing there's something wrong with your computer anyway.

Open a terminal, and enter:
```
gksudo nautilus
```

---

