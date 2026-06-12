---
title: "Beagleboard Packages"
date: 2010-12-09
forum: New to Ubuntu
---

### Post by shalbert on 2010-12-09
Hi!

I'm working with Maverick 10.10 on a BeagleBoard revC4 with no internet connection.  I need to install some packages manually but when I search the repo, the only architectures listed are AMD64 and i386 (and sometimes powerpc or all).  When I had Angstrom, it would have separate packages for ARM architectures so I'm a little confused.

Does anyone know which architecture I should be choosing?

Thanks!


Shannon

---

### Post by Chesamo on 2010-12-09
If the ARM were to be anywhere, it'd be in the "all" packages. Otherwise, you just might have to compile it yourself from source.

Ångström is a distribution specifically designed for integrated devices (such as the BeagleBoard), and Ubuntu is designed as a desktop/server operating system. If the lack of archetectural options is a problem, you may want to consider switching back.

I don't recommend this lightly, though. Ångström is really the best suit for your device -- Ubuntu, in this case, is not the best option.

---

### Post by shalbert on 2010-12-09
I'm finding Angstrom to be unstable and I can't compile anything under Ubuntu because gcc isn't installed and the gcc package does not have an "all" option.  In Ubuntu, the package manager lists that gcc is available for install if I had internet so it must be available somewhere I'm just not sure how to get it.

---

### Post by Chesamo on 2010-12-10
[http://packages.ubuntu.com/maverick/gcc](http://packages.ubuntu.com/maverick/gcc)

Start here, then install all of the dependencies.

---

### Post by shalbert on 2010-12-10
Thanks :)  But that sends me back to my original issue.  Only the packages for amd64 and i386 architectures are listed.  I need the one for ARM and I don't know if one of these is compatible or not.

---

### Post by Chesamo on 2010-12-15
Oh. Wow. That's an interesting oversight.

Apparently the ARM archetecture is no longer officially supported. I don't know what to tell you then -- ARM is not compatible with the x86 or x64 packages (since it's a totally different processor archetecture).

---

