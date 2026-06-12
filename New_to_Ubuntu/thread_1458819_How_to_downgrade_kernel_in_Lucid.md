---
title: "How to downgrade kernel in Lucid?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by ihmemies on 2010-04-20
I got this graphic glitch on my laptop, and its a problem with kernel, as I found out in this thread: [http://ubuntuforums.org/showpost.php?p=9140982&postcount=6](http://ubuntuforums.org/showpost.php?p=9140982&postcount=6)

---

### Post by jaco223 on 2010-04-20
> **ihmemies said:**
> I got this graphic glitch on my laptop, and its a problem with kernel, as I found out in this thread: [http://ubuntuforums.org/showpost.php?p=9140982&postcount=6](http://ubuntuforums.org/showpost.php?p=9140982&postcount=6)

Do you have another kernel installed? Download the old one via Synaptic. Just search for "linux-kernel" install it and you can reboot into the old kernel.

If you  want to remove a kernel from your system, I would advise using Ubuntu Tweak to uninstall a kernel.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Hope this helps.

Jaco

---

### Post by ihmemies on 2010-04-20
I allready did a search using aptitude, and only got this as older:
linux-image-2.6.31-10-rt   
Linux kernel image for version 2.6.31 on Ingo Molnar's full real time preemption patch

It sounds some special kernel, so didnt install it just yet. Wanted to make sure its safe :)
I also found this link, but are those older ones compatible with Lucid Beta 2?
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")

---

### Post by Didius Falco on 2010-04-20
I'm curious as to what appears on your Grub menu at boot. Have you been removing kernels as soon as new ones appear? If you haven't, I'm betting you already have more kernels than you realize...

---

### Post by oldos2er on 2010-04-20
2.6.31.* kernels are for Karmic (9.10). I'm uncertain whether or not they'd work properly with Lucid.

---

### Post by ihmemies on 2010-04-21
> **Didius Falco said:**
> I'm curious as to what appears on your Grub menu at boot. Have you been removing kernels as soon as new ones appear? If you haven't, I'm betting you already have more kernels than you realize...

 I only have the default kernel that was installed on Beta 2, nothing else. But it has problems with my chipset and creates graphical glitches randomly, supposedly 2.6.31 doesnt have this problem so was thinking to downgrade to it until new ones are fixed.

---

### Post by ihmemies on 2010-05-04
OK, I finally found a answer for this problem! Either install 2.6.31 RT kernel, I dont know if this is some weirdly optimized kernel for special purposes, but it did work for me and the graphical glitches were gone. I used it for a week without problems.

Or give kernel parameter **i915.powersave=0** in grub to fix this issue on newer kernel versions. Hopefully this problem will be solved in near future, but this bug is still on 34RC kernels.

---

