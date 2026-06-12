---
title: "how to make terminal &quot;forget&quot; recent commands?"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by werty2010 on 2011-05-05
when we use terminal usually we use the up/down keys to re-execute various commands, because terminal has the ability to remember them.
i'd like to know how to make terminal forget all the commands typed until this moment and remember all the rest for the future.
some help doing that please....?

---

### Post by r-senior on 2011-05-05
The first command deletes all history prior to starting the current shell. The second clears the in-memory history of the current shell.

```
rm -rf ~/.bash_history
history -c
```

The in-memory history is written out to .bash_history when the shell exits.

---

### Post by werty2010 on 2011-05-05
thanks a lot
worked like a charm

---

