---
title: "juat updated ubuntu"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by LunaticHiatus on 2008-12-20
I just installed ubuntu on to a new computer but now when I boot up it shows the version before I updated and the version after. How do I get rid of the old one?

---

### Post by taurus on 2008-12-20
You mean GRUB shows two kernels, the old one and the new one?  It's a good idea to keep the old one around in case there is something wrong with the new one.  But if you really want to remove it, go into System -> Administration -> Synaptic Package Manager -> Quick Search and search for it.  Then, remove it from there.

---

### Post by LunaticHiatus on 2008-12-20
why would I need the old kernal? Isn't that what safemode is for?

---

### Post by taurus on 2008-12-20
Safemode (or recovery mode) still uses the new kernel!  Look at the kernel version.  Again, if you want to remove the old kernel, do it from synaptic since it's the easiest way.  There is nothing wrong with it if you don't want to keep it around.

---

### Post by LunaticHiatus on 2008-12-20
Well, Its actually the same kernal, Since its a brand new install but its separated like its a different kernal

---

### Post by drs305 on 2008-12-20
Here is the link to a tutorial about seeing multiple kernels and the options you have to deal with them:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

If it's the same kernel I don't know if StartUp-Manager can deal with that by setting display options but there is also some information on editing grub manually.

---

