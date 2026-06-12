---
title: "Simple question about liveCD recovery"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by humphreybc on 2009-09-03
Hi,

When using the liveCD, how do I make MY filesystem the root filesystem on the liveCD?

ie. I have MY files mounted at /media/disk on the liveCD, and I want to run a script that uninstalls some [unruly ATI drivers]("http://ubuntuforums.org/showthread.php?t=1256855") but I cannot run the script without my root filesystem being mounted at / and not /media/disk.

What's the command to make /media/disk my root directory?

---

### Post by davetv on 2009-09-03
sudo chroot /media/disk

---

### Post by humphreybc on 2009-09-03
> **davetv said:**
> sudo chroot /media/disk

Thanks, i'll have to remember that. One more question - doesn't this mean that there is a big security flaw in that anyone with a liveCD and physical access to your computer can read and change any files on your computer?

---

### Post by davetv on 2009-09-03
not sure on that one ... guessing so ... i could reinstall os for example

---

### Post by wojox on 2009-09-03
Anybody with physical access to any computer is a security risk.

---

### Post by aeiah on 2009-09-03
if you're worried about physical access, you should encrypt your entire hard drive (save for the /boot partition). probably overkill for most users though

---

### Post by fahadsadah on 2009-09-03
Even without a live CD, there's a security risk.
Boot it into recovery mode, and you have a root shell. Even bypasses disk encryption.

Someone you don't trust should not have access to your computer. If they do, consider setting a boot password in the BIOS.

---

### Post by wojox on 2009-09-03
To reset the password in BIOS all you need to do is reset the jumper on the motherboard.

---

### Post by philinux on 2009-09-03
Physical access means zero security.

---

### Post by LewRockwell on 2009-09-03
> **philinux said:**
> physical access means zero security.

+ 1

.

---

