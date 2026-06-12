---
title: "Recovering openSUSE after installing Ubuntu"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by isaacj87 on 2009-09-25
Hey all,

I was having some trouble recovering my installation of openSUSE 11.2-m7 after installing Ubuntu Karmic alpha 6 side-by-side with it. Usually, I would just into '/boot/grub/menu.lst' but apparently things have been changed with in the introduction of GRUB2. Could anyone help me in getting openSUSE back on my GRUB menu?

Thanks in advance

---

### Post by Liolikas on 2009-09-25
I thik it is hard question for many of us...just try to read:
[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)
I am reading too. :)

---

### Post by fraser_m on 2009-09-25
Try doing:
```
sudo grub-mkconfig
sudo grub-update
```

---

### Post by Incendia on 2009-09-25
> **fraser_m said:**
> Try doing:
```
sudo grub-mkconfig
sudo grub-update
```

I had the same problem before; and that worked for me. :]

---

### Post by isaacj87 on 2009-09-25
Thank you for all the help. I will give that a shot :)

---

