---
title: "Kernels"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by Rayve on 2009-10-23
Just a curiosity question - I finally got Linux properly dual-booted with it's own partition, instead of Wubi, but now when I start up my desktop I see several kernel options -

2.6.28-16 generic
" " - safe mode
2.6.28-15 generic
" " - safe mode
2.6.28-11 generic  <---- first one I installed via LiveCD
" " - safe mode

Is there any way to clean this up and just leave the latest kernel?  Should I even do that, in the event I need to start an older kernel?  New to Linux, not 100% clear on kernels. :)

Thank you!

As an aside: before you do crazy sound-problem work-arounds and spend hours reading threads... do more than just check the volume level from the upper right hand icon.  Try System > Preferences > Sound and route everything through your headset.  /facepalm

---

### Post by qamelian on 2009-10-23
You can use Synaptic Package Manager or any of the other package management tools to remove extra kernels, but it is usually a good idea to keep at least one prior to the latest just on the off chance that a kernel upgrade creates problems.

---

### Post by Paqman on 2009-10-23
The package name will be linux-image-2.26.whatever-generic, just uninstall it and it'll clean up Grub's menu list as well.

It's a good idea to clean out old kernels if you're short on storage, as they're about 100MB each.

---

### Post by qamelian on 2009-10-26
> **Paqman said:**
> The package name will be linux-image-2.26.whatever-generic, just uninstall it and it'll clean up Grub's menu list as well.

It's a good idea to clean out old kernels if you're short on storage, as they're about 100MB each.
They're not that big. My /boot is on a separate partition and is only 100MB. I have 7 kernel versions installed and still have space to spare.

---

### Post by oldos2er on 2009-10-26
> **Paqman said:**
> The package name will be linux-image-2.26.whatever-generic, just uninstall it and it'll clean up Grub's menu list as well.

It's a good idea to clean out old kernels if you're short on storage, as they're about 100MB each.

  Odd. My 9.04 kernels are only 3.4MB each.

---

