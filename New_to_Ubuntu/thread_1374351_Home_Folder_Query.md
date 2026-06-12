---
title: "Home Folder Query"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by cnj on 2010-01-06
When I login to the terminal I expect to see my home folder as colin@Home:~$. However it appears as colin@Home-desktop:~$. Is this right and if not how do I get back to what it should be?

---

### Post by marshmallow1304 on 2010-01-06
Home-desktop is the name of your computer.  The ~ indicates that you are in your home directory.  If you issue
```
ls
```
you can see that, among other things, it contains a Desktop directory.


Edit: The structure is <user>@<computer name>:<current directory>$
Edit2: If the user is root, the $ is replaced with #

---

### Post by tom.swartz07 on 2010-01-06
> **cnj said:**
> When I login to the terminal I expect to see my home folder as colin@Home:~$. However it appears as colin@Home-desktop:~$. Is this right and if not how do I get back to what it should be?

If this is through SSH, then thats normal- that should be the name of the computer. Home-desktop could be the name of the computer that you are logging in to.

If this is the terminal ON the computer, physically accessing the computer, then it seems something is up. You could change that setting from edit>profiles and change the settings on the default profile.



Hope this helps!

---

### Post by sisco311 on 2010-01-06
Home-desktop is the host name, tilde (~) refers to your home directory.

---

