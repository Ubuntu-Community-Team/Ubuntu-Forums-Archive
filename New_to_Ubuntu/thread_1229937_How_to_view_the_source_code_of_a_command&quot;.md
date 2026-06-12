---
title: "How to view the source code of a command?&quot;"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by yygyt on 2009-08-02
How can I see the implementation of a command in Linux? For example, if I want to see the source code of *chmod*, where should I look at?

---

### Post by cwsnyder on 2009-08-02
You are first going to have to load the source modules for the command.  chmod, for example, will probably be in one of the kernel source modules.  This will probably be in the linux-source package or in the binutils-source package.  Depending on whether the command is a core part of the Linux kernel or an add-on, it may be in its own source package, or included in an catchall source package.  Check the man pages for a hint as to where to find the source.

Remember, if you want to change anything, you will also need the full development package of gcc to compile the source.

---

### Post by hyperAura on 2009-08-02
so u dont have to compile the whole kernel but just the source code for the change u made?? cause i think big problems may be caused be recompiling the whole kernel..

---

### Post by cwsnyder on 2009-08-02
If you make a change to kernel code, you _must_ recompile the **whole kernel** successfully for the change to take effect.  Of course, if you make an incorrect change which compiles, you may have a messed up kernel and have to re-install Ubuntu to get back to where you were.

This is not for the faint of heart, or the inexperienced.  If you are going to crash something, maybe you had better start on an application, rather than a kernel.

---

### Post by CatKiller on 2009-08-02
chmod is included in the coreutils package. If you've got the appropriate source entries in your sources.list, you can use ```
sudo apt-get source coreutils
``` to download the source to the current directory.

---

