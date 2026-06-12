---
title: "booting directly into bash in 10.04"
date: 2010-07-08
forum: New to Ubuntu
---

### Post by Chris1274 on 2010-07-08
I'd like to configure my boot sequence to boot into the shell, but the commands given in *Beginning Ubuntu Linux* aren't working. Here's how they say to do it:

sudo rm /etc/rc3.d/S30GDM

gksu gedit /etc/inittab/

adding ...

id:3:initdefault:

to the top of the file and saving.

But the first command returns this response:

rm: cannot remove '/etc/rc3.d/S30GDM' : No such file or directory.

The book was revised with Jaunty in mind, so are things different when it comes to changing the boot sequence in Lucid?

---

### Post by gzarkadas on 2010-07-08
From what I see in my system's /etc (9.10) starting from Karmic, gdm is an upstart service and there is no corresponding SysV script in /etc/rcX.d/  (X=1,2,3,..,etc).

If settings in lucid are the same, then I think that editing the file **/etc/init/gdm.conf**  and changing this line:
```
stop on runlevel [016]

```to this:
```
stop on runlevel [01**3**6]

```and then applying the rest of the guide for setting the default runlevel to 3, will do the job.

Never actually tried it though; be warned :P.

---

