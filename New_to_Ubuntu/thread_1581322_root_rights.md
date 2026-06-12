---
title: "root rights?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by kallekn on 2010-09-24
I am trying to modify a keyboard layout, but it seems I don't have sufficient rights to edit the file. I suppose I need to log out, and then log in with root rights or something, but how do you do that?

---

### Post by bodhi.zazen on 2010-09-24
use sudo / gksu

```
sudo -e file_to_edit
```

```
gksu gedit file_to_edit
```

See also 

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Dustin2128 on 2010-09-24
alternately, you could ```
gksu nautilus
``` then you'd have a small file browser where you had total root privileges; just in case you need to edit additional files or something.

---

### Post by bodhi.zazen on 2010-09-24
> **Dustin2128 said:**
> alternately, you could ```
sudo nautilus
``` then you'd have a small file browser where you had total root privileges; just in case you need to edit additional files or something.

You should use gksu for graphical applications, see the link I gave above =)

---

### Post by Dustin2128 on 2010-09-24
> **bodhi.zazen said:**
> You should use gksu for graphical applications, see the link I gave above =)
*eyebrows raise*
thanks for the link, I should probably stop using sudo for graphical apps now.
fixed the code thing.

---

### Post by bodhi.zazen on 2010-09-25
> **Dustin2128 said:**
> *eyebrows raise*
thanks for the link, I should probably stop using sudo for graphical apps now.
fixed the code thing.

Thank you. Although sudo will work, gksu prevents breakage ;)

---

### Post by kallekn on 2010-09-25
Thanks, worked fine, now I have a nice new Russian keyboard layout.

&#1103;&#1096;&#1077;&#1088;&#1090;&#1099;&#1091;&#1080;&#1086;&#1087;&#1102;

---

