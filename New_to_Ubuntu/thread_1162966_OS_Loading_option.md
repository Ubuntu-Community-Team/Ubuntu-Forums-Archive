---
title: "OS Loading option"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by robertron76 on 2009-05-18
[LIST]
[*]Ubuntu 8.04.2, kernel 2.6.24-24 generic
[*]Ubuntu 8.04.2, kernel 2.6.24-24 generic [recovery]
[*]Ubuntu 8.04.2, kernel 2.6.24-16 generic
[*]Ubuntu 8.04.2, kernel 2.6.24-16 generic [recovery]
[*]Vista recovery
[*]Vista OS
[/LIST]

By default, the first option or Ubuntu-24 is loaded, if there's no change in the selection within 8 seconds.

How do I make Vista OS, the last option as default and choose others manually, by highlighting the specific option?

TIA

---

### Post by skymera on 2009-05-18
You can use startup-manager (From repos)

---

### Post by taurus on 2009-05-18
You can edit /boot/grub/menu.lst manually and change the **default 0** to whichever entry for your windows.  Remember, each title is counted as 1.

```
gksudo gedit /boot/grub/menu.lst
```

Or you can install startupmanager and use it to configure your boot up menu then.

---

### Post by juancarlospaco on 2009-05-18
If you are on Ubuntu, Press ALT + F2, paste this line and press ENTER or click RUN :

```
**xterm -e "sudo cp --verbose /boot/grub/menu.lst /boot/grub/menu.lst.backup ; sudo gedit /boot/grub/menu.lst"**
```

and search for " default		0 " on this configuration text, 
change it for 1, 2, 3, you go from 0=the first one by adding 1 more on the menu items.

---

