---
title: "How to find the UID for my sda2"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by longtom on 2009-04-24
Hi,

I'd like to add a permanent mount to my fstab.  I think I got the principle, but I can't find out how to get the UID for my partition I want to mount.

Can somebody nudge me into the right direction please?

---

### Post by mbzn on 2009-04-24
Please correct me if I'm wrong.
UID is for User-ID, I think it has got to do with the privileges on your mount...

---

### Post by mcduck on 2009-04-24
> **longtom said:**
> Hi,

I'd like to add a permanent mount to my fstab.  I think I got the principle, but I can't find out how to get the UID for my partition I want to mount.

Can somebody nudge me into the right direction please?

I suppose you mean UUID (not UID)?

Just use the "blkid" command, it will list UUIDs for all your partitions.

---

### Post by longtom on 2009-04-24
> **mcduck said:**
> I suppose you mean UUID (not UID)?

Just use the "blkid" command, it will list UUIDs for all your partitions.

Yes - that is what I meant, Thank you.

And thanks for the command, that did the trick.

---

