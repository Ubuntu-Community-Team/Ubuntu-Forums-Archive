---
title: "uuencode help"
date: 2011-09-01
forum: New to Ubuntu
---

### Post by bneva on 2011-09-01
I downloaded "sharlibs" from the package manager and I can't figure out how to use uuencode.  The examples I found seem to be like this

```
uuencode pic.jpg pic.jpg | mail -s "foo" email@email.com
```

I believe the first argument is the file and the 2nd is what you want it to be saved as?  I tried that but it just mail I guess the converted picture in text form?  Something like BEGIN X739CX7YDSYAJD27D etc...

How do I get it to mail the actual picture?

edit: I have no clue what I am doing different but now it works! lol

---

### Post by Paddy Landau on 2011-09-04
To find out what a command does, use *man* (i.e. "manual"):
```
man uuencode
```Sometimes *info* will work:
```
info uuencode
```And sometimes *-h* will work:
```
uuencode -h
```You can also turn to Google.

---

