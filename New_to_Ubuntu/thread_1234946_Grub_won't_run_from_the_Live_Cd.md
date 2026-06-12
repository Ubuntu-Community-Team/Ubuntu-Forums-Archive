---
title: "Grub won't run from the Live Cd"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Warpnow on 2009-08-08
So, I installed windows xp on an NTFS partition, now need to access grub from the live cd in order to be able to restore it. I need to get to a grub prompt, but...it just won't load.

ubuntu@ubuntu:~$ sudo grub



...and nothing. Blank white, no response from any command.

Any ideas?

---

### Post by rohitvk on 2009-08-08
this will sound stupid
but try logging into root ($ sudo passwd)
and then just try 
# grub

---

### Post by louieb on 2009-08-08
Sometimes it takes a few minutes before the GRUB prompt to show up. 
You should be getting this message while waiting for GRUB to load.  
```
Probing devices to guess BIOS drives. This may take a long time.
```

If your not getting the message I would guess there is something wrong with your live CD. Have you scratched it? I'd burn another and check the media for defects. Then try again.

---

### Post by LewRockwell on 2009-08-08
> **Warpnow said:**
> Any ideas?

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

learn to love the grub

.

---

### Post by Warpnow on 2009-08-09
I left to watch TV, came back, and tried again, and it worked immediately.

I have a theory that it had something to do with my hard drive having been browsed, but could be wrong.

---

