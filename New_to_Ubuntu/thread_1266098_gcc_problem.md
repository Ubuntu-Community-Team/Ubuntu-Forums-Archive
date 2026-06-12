---
title: "gcc problem"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by lanzcc on 2009-09-14
Greetings,

When I first tried to use the gcc-4.3 C compiler, it resided in the usr/bin, and it could not write an output file - permission denied.

So I ran gksudo, and then I had permission, but the permission lasted only for that session.

I would like to be able to compile C programs in the directory where I live so I just bodily moved gcc-4.3 to my main Ubuntu directory.

THEN when I tried to compile, the error received was input file format not recognized.

BUT I just used gedit to create a txt file.

WHAT should I have done?

THANKS IN ADVANCE :confused:

---

### Post by sunchiqua on 2009-09-14
Save your file as source.c and try again ( extension is vital ).

```
gcc source.c -o output
```

---

