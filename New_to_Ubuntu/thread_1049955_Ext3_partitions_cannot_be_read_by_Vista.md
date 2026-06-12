---
title: "Ext3 partitions: cannot be read by Vista"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by Shippou on 2009-01-25
Hello...

I have tried installing Ext2ifs, but then, Vista says that the partition should be reformatted. 

Do you know of any workarounds? I would be glad if this wouldn't include reformatting the Ubuntu partition with NTFS as the file system.

Please help.

---

### Post by lswest on 2009-01-25
> **Shippou said:**
> Hello...

I have tried installing Ext2ifs, but then, Vista says that the partition should be reformatted. 

Do you know of any workarounds? I would be glad if this wouldn't include reformatting the Ubuntu partition with NTFS as the file system.

Please help.

First off, you can't reformat Ubuntu's root partition to NTFS, Linux won't run then.  Secondly, did you clean shut down from Ubuntu last time? (read: shutdown using the button, not pushing the power button, etc.).  Also, did you reboot after installing ext2ifs?

---

### Post by starcannon on 2009-01-25
Shippou:
Please take a look at this link:
[http://www.fs-driver.org/faq.html#not_sup_feat](http://www.fs-driver.org/faq.html#not_sup_feat)
and the work around your looking for is to create a fat32 or NTFS(your choice) shared partition. Save things you want to share between linux and windows in this partition, and access problems are solved; while a bit tedious, this seems to be the best way I have found to get Windows to be compatible with other operating systems (irony is a cruel bitch no?)
GL
Rob aka starcannon

lswest, I think he's having trouble reading his ubuntu partition from Vista, doesn't sound like anythings been hosed up yet.

---

### Post by Shippou on 2009-01-25
> **lswest said:**
> First off, you can't reformat Ubuntu's root partition to NTFS, Linux won't run then.  Secondly, did you clean shut down from Ubuntu last time? (read: shutdown using the button, not pushing the power button, etc.).  Also, did you reboot after installing ext2ifs?

Sorry for the mispost. I mean the common partition, not the root.

Oh well, I'll just change the common partition's file system to NTFS...

Vista sucks. This works in Windows XP. Even in SP3.

Anyway, this is on my friend's laptop, running Windows Vista Premium.

---

### Post by lswest on 2009-01-27
> **starcannon said:**
> lswest, I think he's having trouble reading his ubuntu partition from Vista, doesn't sound like anythings been hosed up yet.

Never said they were hosed, I've had problems where Vista suggested reformatting the ext3 drive I was mounting due to an unclean shutdown.  I remember having a similar issue with Vista, but I cannot for the life of me remember how I solved it.

NTFS shared partition is probably the way to go.

---

### Post by theozzlives on 2009-01-27
I never liked ext2ifs. Do a search for Ext2Fsd-0.46a.

---

