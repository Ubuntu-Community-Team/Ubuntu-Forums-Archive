---
title: "Remove old kernel(s) via command line?"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2009-07-13
Hi!

My server has lots of older kernels on it.  If I have already booted up the latest kernel, is there a way to delete the old ones with the command line? (no GUI)

Thanks in advance!

---

### Post by bodhi.zazen on 2009-07-13
sudo apt-get remove <kernel>

---

### Post by pi.boy.travis on 2009-07-13
Thanks!  That was easier than I expected.

---

### Post by LewRockwell on 2009-07-13
[http://www.ubuntugeek.com/howto-clean-up-your-packages.html](http://www.ubuntugeek.com/howto-clean-up-your-packages.html)

[http://ubuntuforums.org/showthread.php?t=996053](http://ubuntuforums.org/showthread.php?t=996053)

```
sudo apt-get autoremove
```

.

---

### Post by pi.boy.travis on 2009-07-13
OK, now I am being told that I may have to re-run my bootloader [grub].  How might I go about this?

Thanks in advance!

---

### Post by LewRockwell on 2009-07-13
> **pi.boy.travis said:**
> OK, now I am being told that I may have to re-run my bootloader [grub].  How might I go about this?

Thanks in advance!

are you using grub?

on a server?

multi-boot?

.

---

### Post by pi.boy.travis on 2009-07-14
I'm using grub (v1.5, I think), and Ubuntu is the only OS.

---

### Post by LewRockwell on 2009-07-14
> **pi.boy.travis said:**
> I'm using grub (v1.5, I think), and Ubuntu is the only OS.

grub shouldn't be necessary if Ubuntu is the only OS...

strange...

.

---

### Post by pi.boy.travis on 2009-07-14
Ubuntu is the only OS, but something still has to load the kernel and initramfs, correct?

---

### Post by mcduck on 2009-07-14
> **LewRockwell said:**
> grub shouldn't be necessary if Ubuntu is the only OS...

strange...

.

Bootloader is always necessary, not just for dualbooting. You need something to load the OS kernel into RAM to boot the OS, the only difference between Grub and for example NTLDR or winload.exe/Windows Boot Manager (used by Windows, NTLDR in Windows NT variants and WMB in Vista) is that Grub has better support for booting other operating systems than just the one it was made for.

---

### Post by jerome1232 on 2009-07-14
Is it wanting you to do this?

```
sudo grub-update
```

Thought that was done for you /shrug

---

