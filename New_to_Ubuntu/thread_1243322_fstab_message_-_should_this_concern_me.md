---
title: "fstab message - should this concern me?"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-18
I noticed this fstab message today.  Should it concern me?  The "errors" caught my attention.

The message / statement:

# / was on /dev/sda1 during installation          ext3    relatime,errors=remount-ro 0       1

---

### Post by coldReactive on 2009-08-18
> **iaculallad said:**
> Actually, its not an error. The errors=remount-ro option will mount the filesystem in read-only mode if in case problems occur during the mount process which prevents data loss.

Filesystem's way of "Self-Preservation".

Meh

---

### Post by cat2005 on 2009-08-18
So, this "error" statement is normal, correct?

---

### Post by coldReactive on 2009-08-18
> **cat2005 said:**
> So, this "error" statement is normal, correct?

Like the message I quoted, it is NOT an error.

---

