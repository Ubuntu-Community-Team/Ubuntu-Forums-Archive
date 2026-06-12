---
title: "removing a word from a file"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by p.caraglio on 2011-06-23
Is there any way using the terminal to remove a specific word from a file without actually opening up that file.

---

### Post by TeoBigusGeekus on 2011-06-23
```
sed -i 's/placewordhere//g' /path/filename
```
This will remove all instances of the word from the file.

---

### Post by idoitprone on 2011-06-23
> **p.caraglio said:**
> Is there any way using the terminal to remove a specific word from a file without actually opening up that file.

it all depends. Is it a plain text file? Use sed and awk, but be forewarn, the syntax has a decently high learning curve, but you can do some complicated stuff

---

