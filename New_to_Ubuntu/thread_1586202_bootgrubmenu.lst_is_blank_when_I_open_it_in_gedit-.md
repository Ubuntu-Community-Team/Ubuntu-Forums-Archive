---
title: "/boot/grub/menu.lst is blank when I open it in gedit- WHY?"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by tacotime on 2010-10-01
okay, so today I need to edit menu.lst, so I open terminal and type 

sudo gedit /boot/grub/menu.lst

gedit opens, and presents a blank document... WTF?


Why is it doing that? Is it normal? How do I fix it?

Thx in advance-
tacotime

---

### Post by drs305 on 2010-10-01
You are most likely now using Grub2, which no longer uses menu.lst.

The changes to Grub are quite significant. You can review the links in my signature for overviews and guides. G2-Basics and GRUB2 are the primary links describing the new bootloader.

Although it isn't meant for editing (and in fact you can't even as root without changing the r/w properties), if you want to take a look at the new replacement:
```
gksu gedit /boot/grub/grub.cfg
```

---

### Post by sikander3786 on 2010-10-01
It is blank on my system as well :-)

Which version of Ubuntu are you using? I think it is GRUB2. What entries you really want to edit?

```

sudo gedit /boot/grub/grub.cfg

```

Don't edit the file if you are not sure what you are doing or you may leave your system unbootable. I know you knew that :)

---

