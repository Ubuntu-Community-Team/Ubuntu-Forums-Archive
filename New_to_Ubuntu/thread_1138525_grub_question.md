---
title: "grub question"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by deeppow on 2009-04-26
Somewhere I've seen a command that can be added to grub so that when the kernel is updated, it will retain the original pointer to the OS that it will use to start.

I'm searched but just haven't used the right combo of words to find it.  Help appreciated.

Thanks!  :popcorn:

---

### Post by Axis on 2009-04-26
Someone please correct me if I'm wrong, however I belive when you go to update if there is anything that will change the GRUB .lst file, it will ask you if you want to make a new one, edit the current one or something along those lines. Basically all you should have to do is select 'Keep the current one'.

---

### Post by deeppow on 2009-04-26
Don't remember ever seeing that question when updating and I know the count was off after updating on occasion.  I have seen someone indicate a command in the boot menu that automatically redoes the count if needed.

---

### Post by meierfra. on 2009-04-26
> it will retain the original pointer to the OS that it will use to start.

Open menu.lst via

```
gksudo gedit /boot/grub/menu.lst
```
and change

# updatedefaultentry=false

to

# updatedefaultentry=true

---

