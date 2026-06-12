---
title: "Finding a file within the directory"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by SaintGrey on 2010-11-12
I've been using ubuntu for a while yet I'm still unclear how things work. Recently I installed Conkeror via the software center and have been playing around with it. I came across a little error and now for the life of me cannot find where the file itself is located. I need to find it's sql file. Anyone?


PS: I'm sorry if this is in the wrong location.


Edit: I'm looking for "places.sqlite"

---

### Post by TeoBigusGeekus on 2010-11-12
```
find / -name nameoffile.extensionoffile 2>/dev/null
```

---

### Post by SaintGrey on 2010-11-12
> **TeoBigusGeekus said:**
> ```
find / -name nameoffile.extensionoffile 2>/dev/null
```
I'm sorry but I'm terribly new at this. If the file is "places.sqlite" what would the command be?

---

### Post by SaintGrey on 2010-11-12
Nevermind, I believe I got it. Thank you!

---

