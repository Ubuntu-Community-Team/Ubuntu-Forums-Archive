---
title: "two ubuntu partitions, want to delete one"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Fika on 2010-01-12
I had to reinstall ubuntu 9.10 and I thought it would overwrite the old install, at least I intended it to but I ended up with 2 ubuntu's side by side with wondows xp and want to delete the newer ubuntu install. When I go to do it in xp disk utility I can't tell which is which. 

If I boot the ubuntu partition I _want to keep_ and use gparted from there can I safely delete all the other ubuntu's?

Thanks

---

### Post by Baelus on 2010-01-12
> If I boot the ubuntu partition I want to keep and use gparted from there can I safely delete all the other ubuntu's?

If you're currently using the ubuntu you want to keep, its partition will be mounted. Gparted will not allow you to delete it, so yes, you can safely delete the other ubuntu installations.

Something you may run into is a broken grub boot loader, depending on which ubuntu grub looks at for its information. That can be fixed though. A quick search through the forums should give you a lot of material to work with.

---

### Post by tom.swartz07 on 2010-01-12
> **Fika said:**
> I had to reinstall ubuntu 9.10 and I thought it would overwrite the old install, at least I intended it to but I ended up with 2 ubuntu's side by side with wondows xp and want to delete the newer ubuntu install. When I go to do it in xp disk utility I can't tell which is which. 

If I boot the ubuntu partition I _want to keep_ and use gparted from there can I safely delete all the other ubuntu's?

Thanks

Just like the poster above me. Yeah, its certainly safe to do it that way. 

JUST MAKE SURE THAT YOU OPEN A TERMINAL AND TYPE
```
sudo update-grub
```

otherwise, you will not be able to reboot your computer, and it just makes a mess thats harder to clean up.

---

