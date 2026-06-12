---
title: "Can browse from Nautilus but not from CLI"
date: 2014-03-07
forum: Networking &amp; Wireless
---

### Post by ubu88 on 2014-03-07
Hi,

I can access shared WIndows 7 folder from Nautilus but when I type the path in bash it's 'No such file or directory'.

I tried all variants:
bash: cd: smb://Win7/D: No such file or directory
bash: cd: //Win7/D: No such file or directory

Do I need to mount it? Isn't it already mounted if I can browse it from Nautilus?

---

### Post by vasa1 on 2014-03-07
> **ubu88 said:**
> ...
Do I need to mount it? Isn't it already mounted if I can browse it from Nautilus?
I think you need to mount it if you go the pure terminal route. File managers use this: [http://ubuntuforums.org/showthread.php?t=2204350&p=12923231#post12923231](http://ubuntuforums.org/showthread.php?t=2204350&p=12923231#post12923231)

---

### Post by steeldriver on 2014-03-07
If a remote filesystem is currently mounted via Nautilus, you should be able to access it via the CLI as well via the .gvfs private mount point. In 12.04 that's in the user's homedir at ~/.gvfs e.g.

```

$ ls ~/.gvfs/
public on nas-01

```

On later versions, it moves to /run/*username*/gvfs or /run/user/*uid*/gvfs

---

### Post by ubu88 on 2014-03-07
Thank you. I got 12.04 and found gvfs but I get 'Permission denied' from CLI. Maybe because it's hidden.

But I can access it in Nautilus.

If I mount it manually I can access it from CLI.

---

### Post by steeldriver on 2014-03-07
You will get 'Permission Denied' if you try to access it as any user other than the owner (even as root - so no 'sudo'!)

---

