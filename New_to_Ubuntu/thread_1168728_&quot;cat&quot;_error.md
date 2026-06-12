---
title: "&quot;cat&quot; error"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by H.om on 2009-05-24
how can i see the contents of a file whose name contain a space
e.g.
there is a text file named "miss world"

"cat miss world" 
gives an error

---

### Post by mellowd on 2009-05-24
```
cat miss\ world
```

---

### Post by H.om on 2009-05-24
i cant get your answer.Please explain in detail

---

### Post by lloyd_b on 2009-05-24
> **H.om said:**
> how can i see the contents of a file whose name contain a space
e.g.
there is a text file named "miss world"

"cat miss world" 
gives an error

Just quote the file name```
cat "miss world"
```

Lloyd B.

---

### Post by mellowd on 2009-05-24
No detail needed.

type: cat miss\ world


i.e. the \ is telling linux that to read the space as part of the filename.

---

### Post by H.om on 2009-05-24
thankyou very much

---

### Post by drs305 on 2009-05-24
Edit: Too late.

The answer was that you place a \ before any space to tell the computer a space follows but is part of the name.

So you type "miss\ world" and the computer knows it is all one entry as opposed to "miss world" where the computer thinks you have typed two unconnected entries, miss and world.

---

