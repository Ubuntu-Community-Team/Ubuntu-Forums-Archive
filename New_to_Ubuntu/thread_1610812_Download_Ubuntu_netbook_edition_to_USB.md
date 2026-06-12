---
title: "Download Ubuntu netbook edition to USB"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by gatoguts on 2010-11-01
I have the Dell 8.04 Hardy release on my mini Dell netbook and would like to download the new netbook edition to a pen drive, but it does not appear to be possible to do this on my user interface.  Is it possible to do this from terminal?

---

### Post by clive littlewood on 2010-11-01
Hi

System > Admin > Startup Disc Creator

This will see your USB stick if you plug it in before boot.

Hope this helps

Clive

---

### Post by bioterror on 2010-11-01
> **gatoguts said:**
> I have the Dell 8.04 Hardy release on my mini Dell netbook and would like to download the new netbook edition to a pen drive, but it does not appear to be possible to do this on my user interface.  Is it possible to do this from terminal?

Technically it should be possible to do: sudo dd if=image.iso of=/dev/sdX bs=1024

But what I know, mainly Arch Linux supports this

---

