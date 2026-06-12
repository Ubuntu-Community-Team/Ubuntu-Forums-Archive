---
title: "What does linux-kernel-devel link to?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by mac9416 on 2009-05-03
I want to recompile my kernel, and I need linux-kernel-devel. Unfortunately my Ubuntu machine (I'm on XP) is offline. I'm using Keryx to download the software.

Question: What packs does linux-kernel-devel link to?

---

### Post by Alterax on 2009-05-04
Here's what you'll need

build-essential
libncurses5 and libncurses5-dev (so you can run make menuconfig)
kernel source (not just an old wives' tale anymore)

The kernel-package package contains the make-kpkg script that automates a lot of the kernel-building process.

Here's a link to the latest .deb of kernel-package. It's architecture-agnostic, so it shouldn't matter what type of processor you're running it on.

[http://mirrors.xmission.com/ubuntu/pool/main/k/kernel-package/kernel-package_11.015_all.deb](http://mirrors.xmission.com/ubuntu/pool/main/k/kernel-package/kernel-package_11.015_all.deb)

Happy hacking!

---

### Post by Alterax on 2009-05-04
Oh, and lest I forget, here's the link for the instructions, courtesy of HowToForge.

I still go over them from time to time.

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

Ok, I'll go away now...

---

### Post by mac9416 on 2009-05-04
Haha, thanks, Alterax. So I need the latest versions of all these:
[LIST]
[*]build-essential
[*]libncurses5
[*]libncurses5-dev
[*]linux-source
[*]kernel-package
[/LIST]

And with those packages I don't need linux-kernel-devel? I've been getting my compile instructions from _Ubuntu Server Administration_ by McGraw Hill.

Thanks!
-mac

---

