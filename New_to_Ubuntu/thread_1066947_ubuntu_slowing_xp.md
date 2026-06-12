---
title: "ubuntu slowing xp"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by luccidity on 2009-02-11
I installed ubuntu on a second drive on my pc. I have xp home on another drive on my xp. I did a full install of ubuntu.

I noticed after installing ubuntu that xp home ran slower, games and apps plus the net went slower.

I uninstalled ubuntu and found my xp home speeded up and ran as normal.

Did i make a mistake when installing ubuntu or is there some other explanation.

Any help appreciated.

---

### Post by gandaran on 2009-02-11
> **luccidity said:**
> I installed ubuntu on a second drive on my pc. I have xp home on another drive on my xp. I did a full install of ubuntu.

I noticed after installing ubuntu that xp home ran slower, games and apps plus the net went slower.

I uninstalled ubuntu and found my xp home speeded up and ran as normal.

Did i make a mistake when installing ubuntu or is there some other explanation.

Any help appreciated.
how did you install ubuntu? using the wubi installer, inside windows? I believe so, you can't uninstall ubuntu if you install it in a separate partition you have to format the partition and repair grub to get rid of ubuntu and boot windows!
now, I don't know if installing ubuntu with wubi slows down windows but try installing the normal way in a separate partition, it won't interfere with windows xp in any way it's a complete deferent install that has nothing to do with windows, you either boot windows or ubuntu.

---

### Post by luccidity on 2009-02-12
Thanks for the reply, appreciated.

I installed ubuntu from the cd at boot up, and did a full install to spare drive.

I will give it another try. I have a new pc now with only one hard drive. So i will have to partition my drive to put ubuntu on.

---

### Post by donkyhotay on 2009-02-12
If you install with wubi it will use the windows partition. If your windows partition gets full it will slow up due to fragmentation and not enough space in the page file. Because of the size of ubuntu it is likely to fill your drive to this point. As mentioned it's probably best to put ubuntu on a seperate partition in this case and have that on another drive. You can also try defragmenting your drive if that is not an option.

---

### Post by luccidity on 2009-02-13
Thanks for the reply, appreciated.

---

### Post by Alterax on 2009-02-13
If you installed Ubuntu as you said--on a separate drive from your XP installation, using the installation CD, then I'm not all that certain about Ubuntu causing the slowness of the XP installation.  Windows has its own drive; Ubuntu is on its own.  And since Ubuntu doesn't run when Windows is running, that leaves us with the greatest likelihood that it's a Windows problem that only became noticeable after the Ubuntu installation. 

So I recommend treating this as a Windows problem.   Try running a malware scanner on Windows.  There's a good free one called "SpyBot Search and Destroy", available at safer-networking.org.  Whatever scanner you use, let it go through and find/zap the malware, then let us know if the Windows speed issue is still a problem.

---

