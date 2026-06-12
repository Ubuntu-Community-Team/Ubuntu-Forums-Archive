---
title: "Change grub to use new kernel automatically"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-12-05
This has probably been asked before, but I haven't found anything on the forum.

After receiving Ubuntu kernel updates, Grub adds the new entry to its bootup options.

However, Grub does not use the newest one by default. It still uses the old kernel.

That makes me wonder, *"How many people are still using old kernels?"* Surely this is a security issue, too?

Why doesn't Grub change automatically to use the latest kernel? Any non-technical user is almost certain to not notice the change, and to not go update the grub menu's default option.

And, how to you get Grub to use the latest version automatically? In Hardy and Jaunty, I use Startup Manager, but that's a manual process. If I don't do that, the computer still reverts to the old kernel on rebooting.

---

### Post by lswb on 2009-12-05
Have you modified your menu.lst file? My experience has always been that the latest kernel is indeed made the default boot kernel, unless I have customized my menu.lst in some way.

---

### Post by Paddy Landau on 2009-12-05
> **lswb said:**
> Have you modified your menu.lst file? My experience has always been that the latest kernel is indeed made the default boot kernel, unless I have customized my menu.lst in some way.
Hmm, it was changed only with the GUI Startup Manager.

I think you might have answered my question; it won't be applicable to the average non-technical user, then.

Thanks.

---

