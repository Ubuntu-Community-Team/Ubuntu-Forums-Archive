---
title: "Deleting old kernels"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by mesmith on 2010-05-10
When running 8.10, if I wanted to get rid of an old kernel I would do a search on "linux-image-2" which would bring them up on Synaptic.  Then I could do a complete removal via synaptic with one click.  Since Grub was set to only show me two kernels this was just fine.

Now I'm running 10.04 and would like to know if the same removal scheme will work.  I'm fairly certain using Synaptic in the usual way will work, but what about Grub2?  Will it update itself or do I have to modify it somehow?

Thanks.

---

### Post by Elfy on 2010-05-10
Removing the kernels will work in the same way - grub will be updated.

---

### Post by mesmith on 2010-05-10
Thanks.  Does Grub2 have a setting that determines how many kernels to show at startup like Grub did, or will it just show all that it finds.

Thanks again.

---

### Post by emoguitarist06 on 2010-05-10
I would install startup-manager, an easy graphical way to do simple changes in grub & grub2

you can remove old kernels from synaptic packager manager
just search
linux-headers
and remove the older versions

---

