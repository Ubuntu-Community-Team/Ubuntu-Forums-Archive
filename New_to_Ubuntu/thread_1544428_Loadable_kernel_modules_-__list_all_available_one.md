---
title: "Loadable kernel modules -  list all available one"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by EgoGratis on 2010-08-02
How do i list all available LKM on my system. (Not loaded but all available to the system).

---

### Post by Cavsfan on 2010-08-02
If you on Lucid or use grub2, just make sure [COLOR=Blue]/etc/grub.d/10_linux[/COLOR] is executable.
They should all show up in your grub2 menu.

---

### Post by EgoGratis on 2010-08-02
No not different kernel versions. But loadable kernel modules.

For example:

 **lsmod **- list loaded modules

But i would like a list of all available loadable kernel modules that system can use.

---

### Post by Cavsfan on 2010-08-02
Not what OP wanted, see next post...

---

### Post by Cavsfan on 2010-08-02
Here it is:

```
sudo apt-get install module-assistant
sudo module-assistant update
sudo module-assistant list-available
```This will list available ones.

---

### Post by Cavsfan on 2010-08-02
And here is the MAN page for the module-assistant command:

_[http://manpages.ubuntu.com/manpages/lucid/man8/module-assistant.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/module-assistant.8.html)_

---

### Post by EgoGratis on 2010-08-03
Thank you for your answer. I will test this tomorrow.

---

### Post by Cavsfan on 2010-08-03
> **EgoGratis said:**
> Thank you for your answer. I will test this tomorrow.

You are always welcome! :)

---

### Post by EgoGratis on 2010-08-07
I don't think module-assistant is what i am after.

If i do:

**sudo module-assistant list-available**

I get a bunch of modules. But if i do **lsmod** (lists loaded LKM) and compare them. They are not on the list.

Closest thing i found is:

**sudo modprobe --list**

But there must be in some file a list of all available LKM to the system and their correct names?

---

### Post by Cavsfan on 2010-08-07
Check this page out:

_[http://www.s0ftpj.org/docs/lkm.htm](http://www.s0ftpj.org/docs/lkm.htm)_

Not sure if that's what you are looking for, but it may be.

---

### Post by luarwo on 2010-10-12
for the lazy
1) listing them 
```
ls /lib/modules/
```2) find out which one you're using
```
uname -r or uname -a
```3) remove, **be sure they are not the ones you are using!** 

```
sudo apt-get remove --purge 2.6.32-23-*
sudo apt-get remove --purge 2.6.32-24-*
```

---

### Post by EgoGratis on 2010-10-15
LKM are not the same thing as old kernels. Just for clarifying thing out.

---

### Post by Cavsfan on 2010-10-16
These should tell you everything you ever wanted to know about LKMs and then some.

[[COLOR=blue]_Linux Loadable Kernel Module HOWTO_[/COLOR]]("http://tldp.org/HOWTO/Module-HOWTO/")

[[COLOR=blue]_ Loadable Kernel Modules Tutorial_[/COLOR]]("http://www.linuxsolutions.fr/linux-loadable-kernel-modules-lkms-how-to-make-kernels/")

[[COLOR=blue]_Linux Loadable Kernel Modules_[/COLOR]]("http://www.rt-embedded.com/blog/archives/linux-loadable-kernel-modules/")

---

