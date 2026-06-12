---
title: "can't see ubuntu 9.10 in menu.lst"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by PLIACHAS PASCHALIS on 2009-11-09
after upgrading in 9.10 version i can't see ubuntu 9.10 kernel 2.6.31.14 on menu.lst. Any idea?
Thanks

---

### Post by whoop on 2009-11-09
> **PLIACHAS PASCHALIS said:**
> after upgrading in 9.10 version i can't see ubuntu 9.10 kernel 2.6.31.14 on menu.lst. Any idea?
Thanks

If by upgrading you mean clean install, then you don't have menu.lst any more because you now are using grub2

---

### Post by PLIACHAS PASCHALIS on 2009-11-09
no i used the update procedure from system menu

---

### Post by wilee-nilee on 2009-11-09
With a daily of Karmic about 5 days ago it installed with regular grub, on a update with all the repositories ticked on in software sources grub 2 was installed. I suspect that even with a upgrade that grub2 is now part of updates. I don't know the terminal command to find your version of grub or if there is one but look in synaptic to see if grub-pc is installed.

---

### Post by ranch hand on 2009-11-09
To find your version run;
```

grub-install -v

```

---

### Post by wilee-nilee on 2009-11-09
> **ranch hand said:**
> To find your version run;
```

grub-install -v

```

I knew there had to a command for this, good job. ;)

---

