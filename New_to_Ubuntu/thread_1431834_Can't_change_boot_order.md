---
title: "Can't change boot order"
date: 2010-03-17
forum: New to Ubuntu
---

### Post by gzav on 2010-03-17
Hi

I just installed Ubuntu 9.10 (64bits) on my pc with Windows 7 64bits already installed but I can't seem to get Grub to change the default boot order. I edited the grub.cfg file and did an update-grub, I installed startup manager and changed it there, but no can do, the selected option is always the 1st one: ubuntu.

Any help on fixing this?

---

### Post by bloodorange on 2010-03-17
I'm pretty sure you're not meant to edit the grub.cfg file.  Instead, edit the line "GRUB_DEFAULT=0" in "/etc/default/grub", then run "update-grub".  This should work.  Although, I tried to alter the timeout and couldn't seem to make that work.

---

### Post by stoogiebuncho on 2010-03-17
> **gzav said:**
> I just installed Ubuntu 9.10 (64bits) on my pc with Windows 7 64bits already installed but I can't seem to get Grub to change the default boot order. I edited the grub.cfg file and did an update-grub, I installed startup manager and changed it there, but no can do, the selected option is always the 1st one: ubuntu.

A little more information would be helpful for knowing exactly what you want to do.  Do you want to change the actual order that the boot options are listed in (i.e. move the last option to the top of the list), or do you want to just change the default boot option (i.e. have it boot the last option automatically)?

Bloodorange is correct that you should not modify the grub.cfg file, because that file is rewritten every time you run update-grub, so any changes you make there will be overwritten.  Grub2 splits the config options up into several different files, so you may be editing different files depending on what you want to do.

---

### Post by julio.tomaschitz on 2010-03-17
Change to old grub, I think it's much better, and you just change the menu.lst and it's all.

---

