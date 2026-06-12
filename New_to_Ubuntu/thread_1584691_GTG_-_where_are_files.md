---
title: "GTG - where are files"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by edzell on 2010-09-29
Been trying GTG for the first time, in 10.04.

Now I want to start over, delete old data or preferably rename it for future recovery; but where is it?

OR:

Is there any way to run 2 or more instances?

---

### Post by Rubi1200 on 2010-09-30
Try searching for file locations in the terminal:

```
locate gtg
```

---

### Post by Elfy on 2010-09-30
I'd specifically look in your /home.

If there's a folder in there somewhere that will have your data I'd assume.

---

### Post by agent8131 on 2011-05-16
I just worked out the answer to this when migrated from one system to another:

.config/gtg
.local/share/gtg

---

