---
title: "how many kernal versions should i have"
date: 2010-02-05
forum: New to Ubuntu
---

### Post by jrandolph on 2010-02-05
I wonder how many different kernal versions should i have in my grub boot list 

as it sits i have 5 for 9.10
2.6.31-14... -15... -16... -17... -19

should i do something to remove the old ones?

like i said i just wonder
there is no issues with my box

---

### Post by thulefoth on 2010-02-05
It's normal for the updated versions-entries to accumulate.  

I got hit by the 'wubildr' issue and had to plink at the sh:grub> prompt.  I had 2 versions then, and I suspect that following this morning's system-update, I have 3.

I have seen-in-passing discussions of whether the old entries can or should be removed, but won't go there without checking & making sure...

---

### Post by drs305 on 2010-02-05
Generally keep the current one and an older one that you know works. Removing or hiding the others can be done via Startup-Manager for Grub legacy (it hides the extra kernels) or Ubuntu-Tweak (it can remove them).

Near the end of this guide on StartUp-Manager is a discussion of the available options:
[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by QIII on 2010-02-05
My recommendation is to keep at least the last known working kernel prior to the current kernel.

If a kernel has been working for you without problems and a new one is installed during an update, you can fall back to the previously working one if any issues arise with the new one.  

You may keep as many as you want, of course, but there is little need to keep any more than the last previously working one or perhaps the one immediately prior to that.

That is, I usually have the current one and the one immediately prior.  I dump all the older ones.  But you may want to keep one more back just to have in your pocket.

---

### Post by wojox on 2010-02-05
You can run:

```
sudo apt-get --purge remove linux-image-2.6.31-14-generic
```

```
sudo apt-get --purge autoremove
```

Keep doing it for each one but not -19

---

### Post by jrandolph on 2010-02-05
to be honest there is no issue with it being there 
i am not in any need for disk space - i guess with the new update i was just kinda curious why they didnt automatically fall off - i mean jeez how long has it been since 2.6.31-14 relatively speaking of course

---

### Post by QIII on 2010-02-05
They don't "automatically" fall off because nobody is assuming what you want to do with your machine.

They don't hurt being there and they don't take up much room.  I just like to clean the garage once in a while.

---

### Post by jrandolph on 2010-02-05
hilarious - everyone likes a clean garage
thanks

---

### Post by lykwydchykyn on 2010-02-05
Realistically you only need one version of the kernel.  It doesn't hurt to keep the old ones, but if your current version is working fine the old versions are just eating up space.

And between the kernel, modules, and headers an old kernel can take up a lot of space on the / partition.

You can remove kernels using Synaptic or your favorite package management utility.  Just deleting them out of /boot or commenting them out of /boot/grub/menu.lst is not a good idea, because it will leave a lot of junk on the system (basically, the headers and modules).

Kernels are in the package manager as linux-image-<version>.  Just don't uninstall your current running kernel!

---

### Post by jrandolph on 2010-02-05
so when i go about deleting them from synaptic do i delete everything that has the 2.6.31-14... -15 and so on

---

### Post by lykwydchykyn on 2010-02-05
> **jrandolph said:**
> so when i go about deleting them from synaptic do i delete everything that has the 2.6.31-14... -15 and so on

Yeah.  Just not the one you're running now.

---

### Post by jrandolph on 2010-02-05
ok done - and nothin blew up or melted haha
thanks

---

