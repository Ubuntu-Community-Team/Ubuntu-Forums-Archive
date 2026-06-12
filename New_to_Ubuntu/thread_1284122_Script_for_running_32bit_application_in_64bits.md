---
title: "Script for running 32bit application in 64bits"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by ricardo.gloe on 2009-10-06
I have an application which does not run in 64bits. The error msg is: 

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64

Can I create a script to tell it to look in the usr/lib32 folder instead?

Could anyone explain, step by step (I have never created a script before) how to do this?

---

### Post by Eisenwinter on 2009-10-06
You need some sort of emulator, or virtual environment for this.

Try getting the ia32libs.

```
sudo apt-get install ia32libs
```

NOTE: I use Arch, so the package name may differ in Ubuntu. In such case, use the following command:

```
sudo apt-cache search 32 | grep lib
```

---

