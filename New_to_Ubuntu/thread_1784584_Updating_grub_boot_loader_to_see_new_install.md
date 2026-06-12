---
title: "Updating grub boot loader to see new install"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by roses100 on 2011-06-17
I have carried out a fresh install of Ubuntu on spare raw partitions using VirtualBox. It installed fine, but my grub menu or boot loader can't seem to find the new install on the spare partitions.

My current host OS is an older version of Ubuntu stored on different partitions, and I would like to also keep this OS in the grub menu for backup.

Is there a way that I can update/reconfigure the grub menu/boot loader to see the new install?

Thanks!

---

### Post by mister_playboy on 2011-06-17
> **roses100 said:**
> a fresh install of Ubuntu on spare raw partitions using VirtualBox.

This line doesn't make sense to me.  If you installed using Virtual Box, then that install would be a something you run from your host OS, not something you boot the computer into.

---

### Post by ashwani kumar sharma on 2011-06-17
> **mister_playboy said:**
> This line doesn't make sense to me.  If you installed using Virtual Box, then that install would be a something you run from your host OS, not something you boot the computer into.
i had installed xp after installation of ubuntu on other partion now i want both option at the starting ubuntu and xp hpw can i get

---

### Post by roses100 on 2011-06-17
> **mister_playboy said:**
> This line doesn't make sense to me.  If you installed using Virtual Box, then that install would be a something you run from your host OS, not something you boot the computer into.

I'm installing Ubuntu this way because in the past when I've installed using the conventional method I always the 'errno 5' error which stops the install halfway and won't proceed. And to install successfully I will have to start again and attempt several times, which leaves me without a working PC untill I succeed, and this can be hours and days.

I know it has installed successfully to the partitions as I can see the file structures from my host OS. But I just need the grub menu to recognize that there is an OS there and be able to boot into it.

---

### Post by YesWeCan on 2011-06-17
When you install a new OS your existing Grub will not automatically know about it. If this is the problem you  need to tell grub to scan your drives and look for new OSs.
sudo update-grub

---

### Post by roses100 on 2011-06-17
> **YesWeCan said:**
> When you install a new OS your existing Grub will not automatically know about it. If this is the problem you  need to tell grub to scan your drives and look for new OSs.
sudo update-grub

Genius! Thanks YesWeCan, thats solved all the issues I had :)

---

