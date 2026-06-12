---
title: "Question about Karmic grub"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by powel212 on 2009-10-29
In a standard dual boot environment, (win - Karmic, *win installed first*), will the second OS, (win), always be the fifth line in the boot grub loader sequence, (and so therefore be called "4" in line "GRUB_DEFAULT=4" of "/etc/default/grub" ?

In the previous legacy grub, after an update the titles in Grub would sometimes change with additional lines being added. So, I ask the question as I would like to know if this behavior will continue in the new Grub?

I am assuming that because the new grub is script based, when new titles are added to grub they will replace old titles. Therefore maintaining your default boot OS as in this case line 5

I am wondering if I can always expect to be able to run the following* when building machines to end up with a dual boot with win as default?

*Code:

```
sudo gedit /etc/default/grub
```

change "GRUB_DEFAULT=0" to "GRUB_DEFAULT=4" "4" being win

then

Code:

```
sudo update-grub
```

The last line is important as i tried it once without running the grub update command and it didn't stick.

I hope this message is clear and not too cryptic.

Thanks 

Powel

---

### Post by autocrosser on 2009-10-29
If you are talking about grub2--there are several threads in the closed Karmic-testing forum you should read & there is a great tutorial in the Tutorials & Tips forum that "should" be required reading also....Do some searching & you will find what you need....

---

