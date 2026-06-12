---
title: "boot trouble (kernel problem?)"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Toafan on 2011-02-21
Earlier today, I was using ubuntu normally, it went to update, yada yada. All good so far.
I switched over to using a different computer for a while. When I came back, the ubuntu had a black screen and didn't respond. Oh Well, I say to my self, and I reboot. The computer loads up, I go through GRUB, choosing the default option (ubuntu) -- but then it hangs during boot. I tried again, this time without my flash drive plugged in - still nothing. I tried one or two more times, but it still didn't work.
Currently, the machine is sitting there, on but not booted into anything, with some boot-process messages on-screen. The one that has me worried says, "BUG: unable to handle kernel".
My first thought is that I may have rebooted while ubuntu was updating. The other possibility that I can think of is that there's a problem with the kernel itself, however I tried booting other versions of ubuntu with the same problem so I don't think that's it. Any help would be greatly appreciated.
----------
I have an install CD lying around, same version of ubuntu as I originally installed. I'm willing to re-install, but I would need to preserve existing user data. Is this a possibility/possible solution?
===========
Computer info:
this is an antique PC from back when DDR originally came out. I don't know any more about it off the top of my head, but I'm willing to go look.
I have not yet tried to boot from CD

---

### Post by wizard10000 on 2011-02-21
Can you boot to a previous kernel?

---

### Post by Toafan on 2011-02-21
Not from the GRUB menu, no. However :D the question may be moot, as I am typing this reply on the previously non-bootable ubuntu machine. If the problem doesn't re-occur after I reboot I'll just come back and mark this as solved.
Thanks anyways.

---

### Post by deconstrained on 2011-02-21
[Boot to a live disk, chroot, double check everything pertaining to your system configuration and rebuild your initramfs.](http://ubuntuforums.org/showthread.php?t=1691463)

---

