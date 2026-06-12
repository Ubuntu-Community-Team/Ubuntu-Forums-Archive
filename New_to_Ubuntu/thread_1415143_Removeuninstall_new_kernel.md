---
title: "Remove/uninstall new kernel"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by Joel Barnes on 2010-02-24
I removed the 2.6xxx.20 kernel that I had upgraded to and am back running the xxx.19 kernel. I had installed .20 through the packager by enabling the non-standard sources. I removed it by booting back to .19 and removing .20 through the packager. I'm not so worried about .20 still showing up in the GRUB

The problem (I think) is that now Ubuntu still wants to upgrade a bunch of secondary packages that go along with the .20 kernel. Various "-libs", the sticky notes program, gtk, etc. How do I get whatever checks for upgrades to recognize that I'm back running the .19 kernel?

If I can't fix this, then how can I tell which upgrades I need for .19 and which I need to ignore for .20?

(sorry not in front of my PC right now)

Running ubuntu 9.10
AMD-64 x4

Thanks,
Joel

---

### Post by Hospadar on 2010-02-24
well just make sure you don't upgrade the kernel package, and any other packages that get installed will be all good.  No package will ever get installed without it's dependencies, so if you never update the kernel package, nothing that depends on it will get updated.  The reverse is also true, if you upgrade some other packages, they will either:
a) depend on the newer kernel, and when you go to upgrade them it will try to do the kernel as well
b) not depend on the newer kernel (the more likely scenario) in which case you are just fine.

---

