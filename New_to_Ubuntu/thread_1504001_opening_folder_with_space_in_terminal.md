---
title: "opening folder with space in terminal"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by libihero on 2010-06-07
i'm trying to open a folders through terminal, but when i try to open one that has a space in it, it gives me an error.  is there a special way to do it?

---

### Post by WinterRain on 2010-06-07
Replace the space with an underscore.

---

### Post by Breambutt on 2010-06-07
Auto-complete with tab for a convenient way. It'll also change the empty space to the correct syntax (\ before the space).

---

### Post by gvoima on 2010-06-07
Space is a special character and gets interpret as one, so to use it in a filename use a backslash, escape sequence. All characters after a backslash is treated as a normal character.
So, to access a directory foo bar, use the command```
cd foo\ bar
```

Or you can wrap the name inside single or double quotes```
cd "foo bar" or 'foo bar'
```

---

### Post by dFlyer on 2010-06-07
Start typing directory name than use the tab to auto entry the directory name or type firstnameorfolder\ secondnameoffolder of directory should do it.

---

### Post by Joe of loath on 2010-06-07
You could also use the * wildcard, although that doesn't work so well when there is more than one directory with the same beginning.

---

