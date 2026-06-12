---
title: "[SOLVED] Start Emerald?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by efexD on 2009-01-03
I recently installed emerald and loaded a theme into it, but i have no clue how to get emerald started, and to make it start every boot.

---

### Post by mc4100 on 2009-01-03
> **efeXor said:**
> I recently installed emerald and loaded a theme into it, but i have no clue how to get emerald started, and to make it start every boot.

Hit Alt+F2, and type:
```
emerald --replace
```

And to make it start on login, go to System -> Preferences -> Sessions, add a new startup program:

[list][*]Click "Add"
[*]Give it a Name, e.g., Start Emerald
[*]Add the code above to the "command" box
[*]Add a comment if you wish[/list]

---

