---
title: "Disable &quot;recent documents&quot; list in Ubuntu 8.10"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Pappy2003 on 2009-05-03
Is there a way to disable the Recent Documents list under Places menu. I didn't like "My Documents" list in windows and I don't like the "Recent Documents" list in Ubuntu 8.10

---

### Post by ibuclaw on 2009-05-03
The you can't make the menu item disappear, but you can disable it by running:
```
rm ~/.recently-used.xbel
mkdir ~/.recently-used.xbel
```

And the recently used files list will always show "No Items".

Regards
Iain

---

### Post by Pappy2003 on 2009-05-03
Thanks for the response tinivole.
I'm new to linux.
I assume I run that code in Terminal correct?

---

### Post by nandemonai on 2009-05-03
> **Pappy2003 said:**
> Thanks for the response tinivole.
I'm new to linux.
I assume I run that code in Terminal correct?

Sure do :)

---

### Post by mystmaiden on 2009-05-03
Does this same command work in 8.04?

mystmaiden

---

### Post by krzysz00 on 2009-05-03
Probably.

---

### Post by Pappy2003 on 2009-05-03
Thanks tinivole and every one else. That worked like a charm. The recent documents no longer propagates a list. It was something I found irritating maybe because it reminded me of windoze.

---

### Post by ashmew2 on 2009-10-30
Thanks tinivole , Works like a Charm.

---

### Post by Cincinnatux on 2009-11-11
tinivole's instructions also appear to work on Karmic Koala, as I'm sure everyone expected.  Just thought I'd confirm because I can.

---

