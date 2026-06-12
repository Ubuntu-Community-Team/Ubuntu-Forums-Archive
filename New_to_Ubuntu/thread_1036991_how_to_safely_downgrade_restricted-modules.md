---
title: "how to safely downgrade restricted-modules?"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by andresmh on 2009-01-11
After doing this update the brightness of my laptop cannot be adjusted:
linux-restricted-modules-2.6.27-11-generic (2.6.27-11.15) to 2.6.27-11.16
linux-restricted-modules-common (2.6.27-11.15) to 2.6.27-11.16

The 2.6.27-11 kernel itself is not a problem since I had actually done an update to that kernel many days before the restricted-modules packages were updateed.

A quick solution was to use grub to boot using the older kernel, but I want to use the new kernel. Especially since the problem is not with the kernel itself.

Is there a way to downgrade only the offending packages without disrupting anything else?

---

