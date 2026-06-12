---
title: "Visual Effects restarts"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Vichfret on 2009-06-30
Every time I login Visual Effects restarts to none when it should be on extra, what can I do to fix it?

edit
actually it looks like it's ignoring the settings I have in compiz settings manager when it's selected in none but compiz re-enables when I select extra, so, How do I make to select extra on startup if it keeps selecting none?

---

### Post by ~sHyLoCk~ on 2009-06-30
Add this to startup applications in prefernces
```
compiz --replace &
```

---

