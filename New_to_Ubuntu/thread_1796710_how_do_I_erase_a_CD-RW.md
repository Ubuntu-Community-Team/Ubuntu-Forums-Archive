---
title: "how do I erase a CD-RW?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-07-04
When I right click the icon in the taskbar, the only option is "Eject" What's going on? Why doesn't it have an "Erase" option?

---

### Post by Sam White on 2011-07-04
Try right-clicking it in Nautilus, or as its icon on the desktop.

---

### Post by westie457 on 2011-07-04
In Brasero > Tools > Blank......

---

### Post by brawnypandora0 on 2011-07-04
> **Sam White said:**
> Try right-clicking it in Nautilus, or as its icon on the desktop.

How come it doesn't appear as an icon on the desktop?

---

### Post by brawnypandora0 on 2011-07-04
> **Sam White said:**
> Try right-clicking it in Nautilus, or as its icon on the desktop.

Huh? I thought Nautilus is a file manager.

---

### Post by maizuddin35 on 2011-07-04
> How come it doesn't appear as an icon on the desktop?
maybe you the desktop icon is disable. try reconfigure it with gconf-editor.

---

### Post by maizuddin35 on 2011-07-04
> **brawnypandora0 said:**
> Huh? I thought Nautilus is a file manager.

nautilus is like windows file manager also, its sort of like that kinda thing, you still can do some more thing with the nautilus. you even can put/embed terminal in nautilus..

---

### Post by brawnypandora0 on 2011-07-04
> **maizuddin35 said:**
> maybe you the desktop icon is disable. try reconfigure it with gconf-editor.

How do I reconfigure?

---

### Post by 73ckn797 on 2011-07-04
In a terminal enter:
```
gconf-editor
```Click Apps
Click Nautilus
Click Desktop
Check the last selection which will show volumes on the desktop.

You can also go to System/Preferences/Main Menu.
When there select System Tools on the left panel then check Configuration Editor.
The editor will then appear under Applications/System Tools

---

### Post by pme 72 on 2011-07-08
System>Administration>Disk Utility and click on the drive where the disc is located gives me options including "Format Volume - Erase or format the volume". I have used Disk Utility to wipe clean a flash drive but have yet to try it with an -RW disc.

---

