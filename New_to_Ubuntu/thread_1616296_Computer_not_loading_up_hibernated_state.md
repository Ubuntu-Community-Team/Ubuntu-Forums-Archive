---
title: "Computer not loading up hibernated state"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by Yerushalmi on 2010-11-08
Hey folks,

I recently partitioned my swap-only hard drive into an ext4 and a swap partition. This disabled my hibernate, and it took me some time to figure out how to modify fstab to recognize the new swap partition.

So now my computer hibernates successfully (tail -50 /var/log/pm-suspend.log demonstrates as much). But when I turn my computer back on, it doesn't load up the hibernated state; it just starts up normally.

Can anybody help?

Thanks

---

### Post by plucky on 2010-11-08
> **Yerushalmi said:**
> Hey folks,

I recently partitioned my swap-only hard drive into an ext4 and a swap partition. This disabled my hibernate, and it took me some time to figure out how to modify fstab to recognize the new swap partition.

So now my computer hibernates successfully (tail -50 /var/log/pm-suspend.log demonstrates as much). But when I turn my computer back on, it doesn't load up the hibernated state; it just starts up normally.

Can anybody help?

Thanks

Post output of ```
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
```

---

### Post by Yerushalmi on 2010-11-08
> **plucky said:**
> Post output of ```
cat /etc/initramfs-tools/conf.d/resume
cat /etc/fstab
```

I posted here on the forum because earlier this morning nobody in #ubuntu was able to help me; in the last few hours, however, somebody did tell me exactly what to do, and you're right. I hadn't (nor did I know I was supposed to have) updated /etc/initramfs-tools/conf.d/resume. Problem's been fixed. Thanks anyways! :)

---

