---
title: "how the heck do i delete an entry from grub menu in karmic?"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-12-30
can't figure it out since they upgraded to grub 2

---

### Post by theozzlives on 2009-12-30
have you tried:```
sudo update-grub
```If so, try removing the kernel via symantic.

---

### Post by mamamia88 on 2009-12-30
i want to delete another linux distro and remove it from grub menu.  not delete a kernel

---

### Post by ST3ALTHPSYCH0 on 2009-12-30
If you're formatting the partition to get rid of it, you can just run "update-grub"... if that's the only other OS on the system you could also
```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

```

That would make it so that grub doesn't look for any other OSes when you reconfigure grub

---

### Post by mamamia88 on 2009-12-30
> **ST3ALTHPSYCH0 said:**
> If you're formatting the partition to get rid of it, you can just run "update-grub"... if that's the only other OS on the system you could also
```

sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

```

That would make it so that grub doesn't look for any other OSes when you reconfigure grub

ah cool thanks

---

### Post by ST3ALTHPSYCH0 on 2009-12-30
No problem. I ended up writing a script to create a totally custom menu, but I found a how-to to change the naming conventions of the built in scripts, so I may be playing with that tomorrow.

---

