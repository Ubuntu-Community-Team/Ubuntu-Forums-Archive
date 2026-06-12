---
title: "mistake with update grub"
date: 2009-02-18
forum: New to Ubuntu
---

### Post by clapton on 2009-02-18
Hello people.
I do a mistake with a update kernel.
When Kernel updates, I didn't update grub, how can I fix it?
How can add to grub new kernel auto?

THx

---

### Post by drs305 on 2009-02-18
I don't know what mistakes you made to the kernel but I assume you want the kernel you downloaded to be displayed in grub. There are various ways to do this.

The simplest if you aren't dual booting: If you have not made any changes to the default grub menu.lst, the easiest way may be to just regenerate grub. You can make your current menu.lst a backup, and then use update-grub to build a new one:
```

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub

```
It will say it can't find the /boot/grub/menu.lst file. Answer "Y" to generate the new one.

If you want to tweak the grub menu.lst settings, such as to start a specific kernel, change the menu timeout, etc, I recommend StartUp-Manager. See the link in my signature line.

---

### Post by clapton on 2009-02-19
> **drs305 said:**
> I don't know what mistakes you made to the kernel but I assume you want the kernel you downloaded to be displayed in grub. There are various ways to do this.

The simplest if you aren't dual booting: If you have not made any changes to the default grub menu.lst, the easiest way may be to just regenerate grub. You can make your current menu.lst a backup, and then use update-grub to build a new one:
```

sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.backup
sudo update-grub

```
It will say it can't find the /boot/grub/menu.lst file. Answer "Y" to generate the new one.

If you want to tweak the grub menu.lst settings, such as to start a specific kernel, change the menu timeout, etc, I recommend StartUp-Manager. See the link in my signature line.

Solved thx

OFf-topic:
I try change grub to other colours without sucess, only blue and cyan allowed?

---

### Post by drs305 on 2009-02-19
> **clapton said:**
> Ff-topic:
I try change grub to other colours without sucess, only blue and cyan allowed?

If you use StartUp-Manager, you should be able to click on the Blue to expand the color selection. Make sure you also tick the "Use Colors in Bootloader Menu" box.

I can't take a screenshot with the expanded color selection box, but click on Blue and it will expand.

---

