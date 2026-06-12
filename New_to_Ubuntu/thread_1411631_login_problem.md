---
title: "login problem"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-02-20
i am using ubuntu kubuntu and windows xp triple boot loader
sometimes back in kubuntu in the system settings i deleted my account by mistake! is there any other way to retrieve my account back?

---

### Post by SuperSonic4 on 2010-02-20
Your user account?

You can boot into the recovery mode via grub and drop into a root shell

From there
```
useradd -m -G [groups] -s /bin/bash *username*
```

src: [http://wiki.archlinux.org/index.php/Beginners_Guide#Step_4:_Add_a_user_and_setup_groups](http://wiki.archlinux.org/index.php/Beginners_Guide#Step_4:_Add_a_user_and_setup_groups)

---

