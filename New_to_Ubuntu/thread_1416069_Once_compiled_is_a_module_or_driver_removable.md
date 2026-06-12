---
title: "Once compiled is a module or driver removable?"
date: 2010-02-25
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2010-02-25
I have compiled a driver for LM-Sensors into my kernel. However, it doesn't work, or I haven't correctly compiled it. 

How do I uncompile or remove it from the kernel so that I can try again?

Is this safe?

Would another compile -overwrite- the existing file?

---

### Post by HermanAB on 2010-02-25
Howdy,

Modules are, well, modular.  You can list, load and unload them with lsmod, insmod and rmmod.

---

### Post by falconindy on 2010-02-25
The preferred method is to use modprobe, as its a more intelligent program. The default behavior (no flags) is to insert a module. Specify the '-r' flag to remove a module.

---

