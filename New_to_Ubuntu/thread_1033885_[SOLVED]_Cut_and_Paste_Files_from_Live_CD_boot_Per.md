---
title: "[SOLVED] Cut and Paste Files from Live CD boot: Permissions"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by teh_yodeler on 2009-01-07
I wish to move my files to another partition on my hard drive (which is already created).

I have two partitions, sda1 and sda2.

My ubuntu will not boot (shows black screen with the word GRUB, makes horrible screeching noise when any keys pressed) so I am booted into the Live CD.

Is there any way to take permission of these files so I can cut the files on sda1 and paste them into sda2?

It says I do not have permission

I do know the password to the user account if that it necessary

Thank you so much

:confused:

---

### Post by cariboo on 2009-01-07
I would suggest you press Alt-F2 and type:

```
gksu nautilus
```

The will start nautilus as root, you should now be able to copy and paste the files you need.

Jim

---

### Post by teh_yodeler on 2009-01-07
> **cariboo907 said:**
> I would suggest you press Alt-F2 and type:

```
gksu nautilus
```

The will start nautilus as root, you should now be able to copy and paste the files you need.

Jim

Thanks, this is working!

---

