---
title: "X-server error after updating the NVidia Driver"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by nebu on 2009-02-05
I installed the latest N-vidia driver (version 180.22)for the 8M series of GPUs in Ubuntu 8.10 32 bit after closing the X-server. but after installation the x-server stopped working, and i am stuck with the low-grade display, and can not revert back to the older x-server settings and version...  Please help  The link to the version of nVidia driver i installed is here : [http://www.nvidia.com/object/linux_display_ia32_180.22.html](http://www.nvidia.com/object/linux_display_ia32_180.22.html)

---

### Post by Hospadar on 2009-02-05
First off, I would stick with the drivers that come from ubuntu's restricted section.  The pretty much always work and are way easier to install.  That said, if you still feel the need for the latest and hottest drivers, I would suggest using the envy tool to install them.   I'm not sure how envy works for 8.10, but I'd assume just fine.  You'll want to use the 8.04 version.

Download it to your machine, then use it to remove the nvidia drivers you installed (after you install, run "envy" from a terminal), then either use it to re-install your drivers, or better yet, install your drivers from System-Administration-Hardware Drivers.

Setting up your own drivers is always sort of a pain, and that's why the packages exist to make it easy, so take advantage of them!

---

### Post by nebu on 2009-02-05
how do i uninstall the drivers???

---

