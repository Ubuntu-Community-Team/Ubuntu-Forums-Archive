---
title: "Ugrading to Kernel 2.6.34 rc 4"
date: 2010-04-16
forum: New to Ubuntu
---

### Post by lawrencegoodman on 2010-04-16
I use a HP Compaq L2105tm monitor (multi touch), which is not currently supported by Lucid. I believe that it is supported by the latest kernel release though. Can I simply go to this site, [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc4-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc4-lucid/), run the deb files in the right order and upgrade that way?

I notice that this release candidate folder has fewer deb packages that the typical one, i.e. there's not that headers file with the word "all" in it. Is it missing something? Do I get the all deb package somewhere else?

Thanks!

---

### Post by jvc26 on 2010-04-30
You can get builds of the mainline kernel via the Mainline repository of the Kernel Team. See: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds) for information. Note the 'Limitations' of upstream kernels, from above:

> 
Although the mainline kernels are built using the Ubuntu configuration files they do not include any Ubuntu specific drivers, if you use any of these drivers these kernels are likely to fail for you. There is also no restricted modules for these kernels. Finally they are also not modified for a specific Ubuntu release. The further away from your base kernel release you are the more likely that there will be an incompatible userspace interaction which will prevent them working for you. Each kernel is configured using the configuration from the release with which it is suffixed, for example 2.6.34-rc4-lucid is built using the Lucid configurations and most applicable to testing there.

The kernel team does not support these kernels, use them at your own risk.


J

---

