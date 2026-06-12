---
title: "menu.lst doesn't exist! How do I change my resolution at boot?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by coldReactive on 2009-11-07
```
@psumi:/boot/grub$ dir *.lst
command.lst  handler.lst  partmap.lst
fs.lst	     moddep.lst   parttool.lst
```

Notice, no menu.lst. Using [this tutorial](http://ubuntuforums.org/showthread.php?t=258484).

---

### Post by marco123 on 2009-11-07
If your using 9.10 then grub2 is installed which uses grub.cfg: [http://grub.enbug.org/grub.cfg](http://grub.enbug.org/grub.cfg)

---

### Post by mikewhatever on 2009-11-07
Are you using Karmic? If so, do consult [->this manual<-.]("https://help.ubuntu.com/community/Grub2")

---

### Post by LewRockwell on 2009-11-07
no menu.lst file in the new Grub 2 that is installed via 9.10

.

---

### Post by coldReactive on 2009-11-07
I don't want to change the resolution of GRUB, I want to change the resolution of my login manager, which I would think you'd change via menu.lst, but I guess I was wrong.

My login manager is xdm, I can't use gdm.

---

### Post by coldReactive on 2009-11-07
However, there is no xorg.conf either!

---

### Post by Mark Phelps on 2009-11-07
> **coldReactive said:**
> I don't want to change the resolution of GRUB, I want to change the resolution of my login manager, which I would think you'd change via menu.lst, but I guess I was wrong.

My login manager is xdm, I can't use gdm.
You need to read the link that mikewhatever provided. It has a section on setting resolutions with boot splash images.

---

### Post by falconindy on 2009-11-07
> **coldReactive said:**
> However, there is no xorg.conf either!
The absence of xorg.conf doesn't prevent you from generating one with `Xorg -configure`.

---

