---
title: "Upgraded ubuntu and Grub menu is gone!"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by TheWanderingMaverick on 2010-01-15
I had updated Ubuntu Kolola, and restarted. I first selected Ubuntu from the Windows boot menu. Then it went into Grub 2, and the menu is gone! I pressed TAB for commands, but that did not help much. All I would like to know for know is to restore the GRUB menu so I can select my OS. Try to keep it simple if possible. I am not too swift with command-line.

---

### Post by warfacegod on 2010-01-15
Try opening a Terminal and typing this:

```
sudo update-grub
```

hit enter. It will ask for your password, hit enter again after typing your password.

The Terminal can be found in:

Applications> Accessories> Terminal

---

### Post by TheWanderingMaverick on 2010-01-15
I can't get into Ubuntu. I am able to boot XP with no problems. Is there a way to modify grub externally so I can get the menu back? or a command within Grub?

---

### Post by warfacegod on 2010-01-15
I think this should help you better than I can:

[http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub2]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub2")

---

