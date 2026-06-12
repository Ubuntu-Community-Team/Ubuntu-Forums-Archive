---
title: "automatic updates message"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by relic70 on 2009-02-11
The following description appears in the Update Manager for


> linux-ubuntu-modules-2.6.24-23-generic

This package contains modules supplied by Ubuntu for Linux kernel 2.6.24 on x86/x86_64.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.

Ordinarily I would go ahead and install these updates, but I'm curious why the message says - You likely do not want to install this package directly.

Can anyone explain what they mean by this?

Thanks in advance

---

### Post by Seq on 2009-02-11
What it means is that since the modules themselves are useless without the matching kernel, you should probably not be manually installing them -- let the package manager handle installing the proper modules package for your kernel.

The issue you've encountered is that the description of the package is a static field, and the note regarding installation was not meant to discourage you from updating it.

---

### Post by relic70 on 2009-02-11
Thanks Seq,

I knew that particular kernel version was installed on my machine, but was still confused by the message.

---

