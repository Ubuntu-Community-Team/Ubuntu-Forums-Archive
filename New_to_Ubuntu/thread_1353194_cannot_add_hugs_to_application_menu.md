---
title: "cannot add hugs to application menu"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by someNewb on 2009-12-12
when you edit menus (application menu, that is), you are allowed to add your own programs

so i add item, an "application" and under user command i write "hugs". but when i click it, nothing happens

when i manually open terminal and write "hugs" it works. but it doesn't in the menu, why?

**edit:** nevermind, i see i should have picked "terminal application" instead of "applicaton"
but now i have another problem
when i want to associate files with extension .hs to be automatically to be opened by hugs, it does the same thing as if there weren't chosen "terminal" application, it does nothing

in other words, how can i "open file with" some terminal application?

---

### Post by falconindy on 2009-12-12
I'm not a Haskell user, so forgive me if any of this is inaccurate. I'm **assuming** that hugs has no graphical interface. If this is the case, try this instead in the command:
```
gnome-terminal -x hugs
```

---

### Post by someNewb on 2009-12-12
thanks!

---

