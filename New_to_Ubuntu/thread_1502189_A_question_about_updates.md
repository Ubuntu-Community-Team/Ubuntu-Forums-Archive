---
title: "A question about updates"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Blutkoete on 2010-06-05
Hello!

When I update my systems via *apt-get update* and *upgrade*, it downloads (last time on Lubuntu for example) 40 MB and tells me that after the upgrade, 1.4 MB more will be used.

I'm just interested: What's in those 40 MB when only 1.4 MB will remain after the upgrade? Are there 38.6 MB of program code that just tells the system how to compile and where to put those 1.4 MB?

Thank you very much,

Blutkoete

---

### Post by ankspo71 on 2010-06-05
Hi,
It appears to me that they calculate it this way because the files it downloads always overwrites the previous version of the same package (except the kernels and maybe some other things). Updates are almost always larger than the file it replaces, so it tells you how much you need to download, and how much more space it will require after it overwrites the original.

It doesn't include the extra space needed to save the deb files to your hard drive, otherwise the extra space it uses would be a much larger number. These deb files can easily be removed if needed, so that's probably why they don't include them in the calculation.

Hope that helps.

---

