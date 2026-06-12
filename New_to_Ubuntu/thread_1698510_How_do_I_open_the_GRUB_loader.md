---
title: "How do I open the GRUB loader?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Thelinuxgeek on 2011-03-02
i have two hard drives, one for windows, one for ubuntu. when i want to use ubuntu, i press f8 for the bbs popup and select the hard drive with ubuntu on it. it immediatly begins to load the ubuntu os, with no grub loader. for certain reasons, i  need to access the grub loader and edit some stuff. but how do i open it? thanks in advance for all replies.

---

### Post by Vi3tHoneyX on 2011-03-02
[COLOR=DarkRed]Grub is stored in ```
/boot/grub
``` and 
```
/etc/default/grub
```You need to use a command like this to edit the files.

```
gksudo gedit /etc/default/grub
```

Only root can edit GRUB files. :)
[/COLOR]

---

### Post by philinux on 2011-03-02
> **Thelinuxgeek said:**
> i have two hard drives, one for windows, one for ubuntu. when i want to use ubuntu, i press f8 for the bbs popup and select the hard drive with ubuntu on it. it immediatly begins to load the ubuntu os, with no grub loader. for certain reasons, i  need to access the grub loader and edit some stuff. but how do i open it? thanks in advance for all replies.

When ubuntu boots press the shift key to access the grub menu.

To edit what goes into the menu you need to read these.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

