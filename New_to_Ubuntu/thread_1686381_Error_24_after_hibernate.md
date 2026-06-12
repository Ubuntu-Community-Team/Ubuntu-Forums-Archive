---
title: "Error 24 after hibernate?"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by arikshtiv on 2011-02-12
Hi,
I upgraded my ubuntu 10.10 from ext3 to ext4 and everything was fine for a few days, shutting down and booting up.
But one day when I wanted to send ubuntu to sleep instead of shutting it down I pressed hibernate and once I tried booting my computer up I got this error message:
> Error 24: Attempt to access block outside partition

I tried installing grub using:
> sudo grub-install --root-directory=/mnt /dev/sda5
and since that didn't work I tried installing it on the MBR(which made my computer start the grub shell):
> sudo grub-install --root-directory=/mnt /dev/sda

so my ubuntu turned completely unusable after sending it to sleep.
What can I do?

Thank you,
Eric

---

### Post by cariboo on 2011-02-12
Can you start in recovery mode? How big is your swap partition?

---

### Post by arikshtiv on 2011-02-14
My swap is about 1.5GB and I have only 512MB of RAM.
I tried going into recovery mode but it's the same over there too.

I managed finding grub commands and boot into the windows boot loader and fix the MBR using windows.
And then I booted into an ubuntu I installed inside windows and couldn't mount the partition of the broken ubuntu.
So I used a demo version installed inside windows and fixed the file system and managed to backup my files incase I will need to format it and reinstall.

From how I see it I think it's a bug.

But does anyone know how to fix it for now?

Thanks

---

### Post by arikshtiv on 2011-02-22
*bump*

---

