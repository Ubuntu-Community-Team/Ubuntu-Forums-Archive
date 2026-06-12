---
title: "Are there rars that unrar can't unrar?"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by DrMilo on 2010-06-05
Title pretty much explains things. I've got 2 rars that won't unpack with unrar. Not knowing whether it's the rars themselves or that unrar doesn't work on them, I was wondering if there's any other programs out there that I could try that perhaps work with other types of rars.

Thanks in advance!

---

### Post by marshmallow1304 on 2010-06-05
Do you have unrar-free installed?
If so, try switching to unrar.
unrar-free, according to its description, can't handle all rar archives.

If that still doesn't work, try installing p7zip-full and p7zip-rar and extracting the archive like so:
```
7z x rarfile.rar
```

---

### Post by DrMilo on 2010-06-06
Thank you! P7zip did it! Although it seems to assume a path to unpack the files to.

---

### Post by marshmallow1304 on 2010-06-08
I think if you substitute 'e' for 'x', it won't extract to a new directory.  There's a list of operations in the 7z man page.

---

### Post by anewguy on 2010-06-08
Okay, now that the thread is marked as solved, I should be safe adding this without distracting from the thread:

Your title was exactly on point, which I commend.  My weird sense of humor saw something else in it as well, and I just have to reply:

unrar would unrar all the rars if unrar only could


Dave ;)

---

