---
title: "Um, finding files?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by SevenHundred on 2011-08-17
Trying to install DotA. I have WC3 and can play it, but I can't find the file folder for it so that I can put the DotA map in. I have tried 3 different methods of searching and the "show hidden files" option but nothing has worked. Help for a Linux noob?

---

### Post by seawolf167 on 2011-08-18
You can try [CTRL][F] to search in nautilus, or just *find* to search in the terminal

```
man find
```

If you installed the game through Wine, you can manually browse to the folder (I'm not sure what folder you need), but the general location should be something like:

```
cd ~/.wine/drive_c/Program\ Files/
```

---

### Post by whatthefunk on 2011-08-18
In a terminal:

```
locate whatever_it_is_you_want_to_fine
```

---

### Post by SevenHundred on 2011-08-18
Thanks guys, finally found it. Didn't think to look under .wine

---

### Post by seawolf167 on 2011-08-18
No problem - glad you got it solved!

---

