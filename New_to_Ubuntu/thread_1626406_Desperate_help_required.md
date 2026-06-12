---
title: "Desperate help required"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by ian19jam on 2010-11-20
My main computer wont boot up Ubuntu 10.10. I only recently download this onto my computer fom the 10.4 version. When I have switched it goes to motherboard screen and then into the list of choice for selecting Ubuntu 10.10 afterwards it screens the following:

1.267365 KERNEL PANIC-NOT SYNCING; ufs unable to mount root fs on unknown block po,o

then whole rows of numbers with kernel

last linebefore it sticks and wont continue to move 
1.267365 (c010363e) kernel thread-helper &#803;+ ox6/Ox10

Any advice please or is this bad news and the computer is finished> Ihad it rebuilt in 2007.

Thanks

---

### Post by northern lights on 2010-11-20
Have you attempted booting from an older kernel version?

Unless you've reinstalled, older kernel version ought to be selectable from the GRUB menu.

---

### Post by ian19jam on 2010-11-20
Thanks for your response but I dont understand you> I know little about computers  please explain in simple terms

---

### Post by northern lights on 2010-11-20
You updated from 10.04 to 10.10 right?

If that's the case, older kernel versions are still existent on your system but do not get booted by default.

"GRUB" is your bootloader. After your mainboard has gone through its memory and integrated peripheral check and all, before any Ubuntuesque graphics appear on the screen you ought to see a boot menu with several kernel version and Recovery Options. Disregard the latter and pick an older (lower number, lower in the menu) version.

Hope that one doesn't panic.

---

### Post by ian19jam on 2010-11-20
Thanks and it worked but how do i stop this happening again please?

---

### Post by ian19jam on 2010-11-20
Since my last response the computer crashed again and have treid the older kernel number again and it comes up with a screen full of different colours. What do advise they do next please?

---

### Post by northern lights on 2010-11-20
It's beyond the scope of a forum thread to discuss the causes of kernel panics and I have no reasonable guess as to what went awry with you system after the latest update.
Most likely it's some bug / hardware incompatibility with that particular kernel version.
Further Reading: [Wikipedia, The Linux Kernel, Panic Section]("http://en.wikipedia.org/wiki/Linux_kernel#Kernel_panic")

Open a terminal from *Applications > Accessories* and run an update again:```
sudo apt-get update && sudo apt-get dist-upgrade
```Any errors?

Reboot.

See if issue is solved.

If not, keep booting into a working kernel version until new kernel update.

---

### Post by northern lights on 2010-11-20
> **ian19jam said:**
> Since my last response the computer crashed again and have treid the older kernel number again and it comes up with a screen full of different colours. What do advise they do next please?
Darn.

Problem appears to be more deeply rooted, eh? Sorry.

If you get the opportunity to, cause the system works gracefully for a while, still do the above updating.

Boot from a LiveCD. If that crashes too, it's a hardware issue...

---

