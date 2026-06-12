---
title: "swap space"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by aomarsh2001 on 2009-12-28
i have a 3.1GB swap space partition
can i delete this

---

### Post by django0909 on 2009-12-28
Yes, as long as it is unmounted when you're trying to delete. 

Use gparted: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by audiomick on 2009-12-28
This is theoretically possible, but not advisable. The system will theoretically run without a swap space, but this is not recommended.

If you think this is too much space, you can reduced the size of it with gparted. It is probably better to do this from the live CD or a gparted live CD :
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Most people seem to recommend at least 1GB of swap.

If your swap partition is not at least as big as your RAM, hibernate will not work. Hibernate writes the contents of RAM to the swap partition when it puts the computer to sleep.

---

### Post by warfacegod on 2009-12-28
If you use Suspend or Hibernation then; no.

---

### Post by lotharmat on 2009-12-28
> **warfacegod said:**
> If you use Suspend or Hibernation then; no.

Not strictly true..

Suspend will work fine without swap.

Hibernate cannot work without swap as audiomick says.

When you suspend the computer; the system keeps power flowing to RAM so when it wakes up, it does it instantly.

Hibernate dumps the entire contents of RAM to swap and then reloads it again when the computer is woken up.

---

### Post by kansasnoob on 2009-12-28
Also if you resize or move SWAP the UUID's will likely change in /etc/fstab and /etc/initramfs-tools/conf.d/resume so you'll likely lose the quiet slash at startup and SWAP will not be on at boot.

Are you really that badly pinched for space?

---

