---
title: "Change bootloader permanently"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by MaxRabbit on 2008-12-23
I installed Ubuntu on my laptop, but when I tried to launch it I got: Error 21 and something about wrong disc inserted. However, it was an easy fix: by going into the "edit" menu on GRUB by pressing "e", I was able to change the boot (or was it root?) from hd (1,0) to hd (0,0) and that made it boot just fine.

So, my question is: how cam I make it permanently to boot from "hd (0,0)"?

Thanks,
max

---

### Post by pissedoffdude on 2008-12-23
> **MaxRabbit said:**
> I installed Ubuntu on my laptop, but when I tried to launch it I got: Error 21 and something about wrong disc inserted. However, it was an easy fix: by going into the "edit" menu on GRUB by pressing "e", I was able to change the boot (or was it root?) from hd (1,0) to hd (0,0) and that made it boot just fine.

So, my question is: how cam I make it permanently to boot from "hd (0,0)"?

Thanks,
max

You can do this by editing your menu.lst
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by MaxRabbit on 2008-12-23
Thank you; worked like a charm :D

---

