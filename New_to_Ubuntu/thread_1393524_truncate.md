---
title: "truncate"
date: 2010-01-29
forum: New to Ubuntu
---

### Post by morris_shanna@live.com on 2010-01-29
[FONT=Courier New]How do I truncate a file?[/FONT]

---

### Post by blazemore on 2010-01-29
Do you mean take the first few lines?

```
head -n 10 original.txt > truncated.txt
```

will give you the first 10 lines.

---

