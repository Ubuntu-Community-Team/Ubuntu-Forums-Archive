---
title: "Edit GRUB bootloader?"
date: 2009-10-19
forum: New to Ubuntu
---

### Post by designateduser on 2009-10-19
Hey Linux community!
So I was messing around some administration menus, and noticed that I did not see any for GRUB boot-loader. Is there a way to edit GRUB's preferences (backgrounds maybe, what order the partitions are in)? Any insight is much enjoyed.:)

---

### Post by pgar23 on 2009-10-19
You can edit the GRUB menu. You cannot add backgrounds, why would you anyways (you see it for about two seconds while you are selecting which OS to boot into)
```

sudo gedit /boot/grub/grub.conf

```

Be very careful while editing and commenting out things. I have tried this before with disastrous result. Comment out thee wrong line and you can kiss your OS goodbye.

Some of the things that you may be interested in editing in this file may be:
The amount of time you can have to select an OS,
The order of OSs in the menu
You may want to comment out an OS, but be sure you comment out the whole thing, not just one line.

Enjoy, hope this helps.

---

### Post by drs305 on 2009-10-19
You can use StartUp-Manager. It's a great app to tweak Grub (and some of Grub 2). It sets default kernels, timeouts, colors, basic splash screens, etc.

Here is a guide:
[http://ubuntuforums.org/showthread.php?t=818177]("http://ubuntuforums.org/showthread.php?t=818177")

or just click on SUM in my signature line.

---

### Post by sasj15 on 2009-10-31
> **pgar23 said:**
> You can edit the GRUB menu. You cannot add backgrounds, why would you anyways (you see it for about two seconds while you are selecting which OS to boot into)
```

sudo gedit /boot/grub/grub.conf

```Be very careful while editing and commenting out things. I have tried this before with disastrous result. Comment out thee wrong line and you can kiss your OS goodbye.

Some of the things that you may be interested in editing in this file may be:
The amount of time you can have to select an OS,
The order of OSs in the menu
You may want to comment out an OS, but be sure you comment out the whole thing, not just one line.

Enjoy, hope this helps.

I agree with [pgar23]("http://ubuntuforums.org/member.php?u=363780"), there's no need to have something impressed where you just select the OS for 10 seconds or less!

Thanks,

---

