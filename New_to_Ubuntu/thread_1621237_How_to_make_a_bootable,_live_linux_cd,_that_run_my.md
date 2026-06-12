---
title: "How to make a bootable, live linux cd, that run my install.sh?"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by honeybear on 2010-11-14
Hello,

I made a backup of my system, and I would like that my dvd runs install.sh
i.e.

cat install.sh
```

dd if=image_sda_dd_recoverbackup_linuxbox.img of=/dev/sda
# then I run some other install commands 

```

and this completely automatically, I slot the dvd of install of my partition 2gb (it is enough since I use NFS over /home)

Any ideas?

(no remastersys.html would liked)

---

### Post by mr_luksom on 2010-11-14
I have no idea how you could do this with a cd/dvd, however you could do it as a live USB.

If you use unetbootin to create a live USB with persistence, load the programs/configuration files etc onto it, and the set your install script to run on startup.

Maybe you could do the same thing with a RW DVD, I'm not sure.

---

