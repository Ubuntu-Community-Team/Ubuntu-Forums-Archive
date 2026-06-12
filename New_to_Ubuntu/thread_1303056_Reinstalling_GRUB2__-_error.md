---
title: "Reinstalling GRUB2  - error"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by skymera on 2009-10-27
Hi

I'm trying to reinstall this monstrosity known as "grub2" following this:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

i get so far and get this error though:

```
 root@ubuntu:/# sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
Your /usr is broken; please fix it before calling this wrapper
```

I was using Ubuntu 2 days ago and it was fine.

Any help? Thanks.

---

### Post by skymera on 2009-10-27
!fixed!

Well, GRUB-pc package had been removed and replaced with boring ol' grub. This was from Startup-manager.

I downloaded packages through livecd and copied them to my ubuntu mount point and installed them via dpkg. All seems good now.

---

