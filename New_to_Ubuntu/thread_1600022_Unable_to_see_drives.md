---
title: "Unable to see drives"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by AnimalMagic on 2010-10-18
Just installed 10.10 on a dell system 8250 that has an IDE drive plus two sata drives. Sata drives show up when rebooting with a bios display, but Ubuntu doesn't recognise them. Disks were showing under 10.04.

GParted doesn't show anything other than IDE disk.

Sata controller is a silicon image SiI 3112.

Any ideas what could be wrong?

---

### Post by arpanaut on 2010-10-18
Yes this is a bug in the kernel used in maverick:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595321)

One kind soul has constructed a patch and implemented it into the kernel: [https://launchpad.net/~andrew-betts/+archive/ppa-patches]("https://launchpad.net/%7Eandrew-betts/+archive/ppa-patches")

I have been using this kernel for the past few weeks and it works perfectly. It is a little daunting at first to get this going but really prety straight forward, just enable the ppa, then install the four packages within said ppa via Synaptic.  (instructions for ppa on patches page)

Apparently some of the speed tweaks implemented into maverick keeps the sata <silicon image> controller from seeing the drives.  At this time this is the only remedy that I know of.  Hopefully this patch will be implemented into the main kernel soon, or hopefully will not be a problem with natty.

Hope this helps!

PS-> I just noticed your chip 3112 is different than mine 3114 but as I remember these controllers are very similar so this patched kernel should work for you too.

---

### Post by AnimalMagic on 2010-10-18
Thanks, that seems to have done the job.

---

### Post by arpanaut on 2010-10-18
Great!  Now if you could do me and the community a favor?

Log on to launchpad and go to that bug and add yourself to the affects me too at the top of bug page.
Then add a comment that the patch solves the issue and note that your chip is the 3112 controller.
This will bring more attention to the bug and maybe get the patch brought into the main kernel faster, and maybe stop the mistake being made in the future.

Thanks!

---

### Post by AnimalMagic on 2010-10-18
Have done so!

---

### Post by arpanaut on 2010-10-18
You da Man!

Thank you very much.

---

### Post by arpanaut on 2010-10-20
Just a Heads_Up!

If you want to keep this patch working, DO NOT accept the kernel update that came down today 10-20-10.
Go into synaptic and lock the packages from this ppa or you will lose your sata drives again.
Luckily I have a testing install of maverick that I use to make sure updates will not break my system.
After you lock the pkgs. in ppa then all other updates work fine.

As of now this patch has not been put into the main kernel.

---

