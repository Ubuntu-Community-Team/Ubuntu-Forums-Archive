---
title: "Running files with a '('"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by linuxguymarshall on 2009-06-20
I am trying to run the Star Craft installer in wine but I am hitting a road block. I want to run 
```
wine /media/scraft/StarCraft\ (Windows).exe
```The Installer name is 'StarCraft (Windows).exe' and aparently the '(' is giving me trouble as the program wont run and says 

```
bash: syntax error near unexpected token `('
```Any words of advice?

---

### Post by zeroseven0183 on 2009-06-20
**Rename the file** as StarCraft-Windows.exe or simply, StarCraft.exe

---

### Post by linuxguymarshall on 2009-06-20
I tried, but the installer does not work without it being that name.

---

### Post by SOULRiDER on 2009-06-20
Add a backslash before (  and  )

---

### Post by CatKiller on 2009-06-20
> **SOULRiDER said:**
> Add a backslash before (  and  )

Exactly. If you want to accurately type a filename, use tab completion. In this case,

wine /me<TAB>sc<TAB>St<TAB>

will probably suffice.

---

