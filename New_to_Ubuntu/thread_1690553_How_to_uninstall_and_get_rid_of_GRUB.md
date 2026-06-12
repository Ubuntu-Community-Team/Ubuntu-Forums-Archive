---
title: "How to uninstall and get rid of GRUB"
date: 2011-02-18
forum: New to Ubuntu
---

### Post by bigjim01 on 2011-02-18
I installed UBUNTU 10.10 on an external drive and I do like it, but I don't want to invest the time in learning a new operating system. I want to uninstall UBUNTU but I want to be sure that I get rid of the GRUB boot menu too. 

Is there an uninstall command within UBUNTU?  Can I simply format the external drive and wipe it clean? Would that action also get rid of the GRUB menu?

I like the way UBUNTU works but I don't have enough years left to invest in learning enough to be proficient ( I'm 76) so I'm just trapped in Windows World. 

I'll appreciate any advice.

---

### Post by TeoBigusGeekus on 2011-02-18
Format the ubuntu partitions from windows.

_WinXP_
Boot up with a winxp cd and choose r (recovery mode).
Give
```
fixmbr
```
at the command prompt and grub will vanish.

_Win7_
[http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html]("http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html")

---

### Post by bigjim01 on 2011-02-18
Thanks for your reply. Unfortunately, I don't have an install DVD, Windows 7 came pre-loaded on my new computer. I did make recovery disks and I have tried using them. I used the "Startup repair" function several times but this didn't fix the problem. Its beginning to look like I'll have to do a complete recovery if I want to get rid of the Linux GRUB menu.

---

### Post by fabricator4 on 2011-02-19
> **bigjim01 said:**
> Thanks for your reply. Unfortunately, I don't have an install DVD, Windows 7 came pre-loaded on my new computer. I did make recovery disks and I have tried using them. I used the "Startup repair" function several times but this didn't fix the problem. Its beginning to look like I'll have to do a complete recovery if I want to get rid of the Linux GRUB menu.

You don't need to reinstall

Boot off the recovery disk, Select "Repair Computer".
Next window, select "command prompt" at the bottom.

```

c:
cd \boot
bootrec.exe /fixmbr

```

Chris

---

### Post by fabricator4 on 2011-02-19
Alernately you can run it off the CD if it causes you problems.

```

cd \sources
bootrec.exe /fixmbr

```

---

