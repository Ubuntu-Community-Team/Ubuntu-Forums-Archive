---
title: "Transmission won't start"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by dstin1 on 2009-02-09
Worked fine until today and now it just won't start.  Any help would be appreciated.

---

### Post by Temposs on 2009-02-09
Please open Terminal through Applications->Accessories and type:

```
transmission
```

Copy and Paste and text that appears there after you press Enter.

---

### Post by dstin1 on 2009-02-09
Tried that already and the output did not make since to me here it is.

dave@ubuntu:~$ transmission
Couldn't read "/home/dave/.config/transmission/settings.json": Success
transmission: bencode.c:670: tr_bencDictAdd: Assertion `tr_bencIsType( ( dict ), TYPE_DICT )' failed.
Aborted
dave@ubuntu:~$

---

### Post by wolfen69 on 2009-02-09
go to your home folder and do ctrl-H. then find the .config/transmission/settings.json file and delete it. then start transmission. it should create a new file for you.

---

### Post by dstin1 on 2009-02-09
thanks that did the trick.  I was starting to get stressed.

---

### Post by briml3y on 2009-02-23
I have a similar error
```

$ transmission
Couldn't read "/home/brimley/.config/transmission/settings.json": Success
transmission: bencode.c:1370: tr_bencMergeDicts: Assertion `tr_bencIsDict( source )' failed.
Aborted

```
Removing settings.json file fixed the problem thanks!

---

