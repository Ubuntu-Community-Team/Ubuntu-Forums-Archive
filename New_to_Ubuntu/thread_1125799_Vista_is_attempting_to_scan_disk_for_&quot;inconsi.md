---
title: "Vista is attempting to scan disk for &quot;inconsistencies&quot; - should I prevent it?"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Noise... on 2009-04-14
I know there are issues with Vista not playing nicely with other OS's. When I boot into Vista, for a brief moment a message comes up stating that Windows is scanning my hard drive to check for inconsistencies. I usually press a key to cancel, as I don't want Vista messing with my partitions or Ubuntu. 

What is Vista trying to do here? Should I be worried?

---

### Post by oldsoundguy on 2009-04-14
that usually means that you did not shut something down PROPERLY (according to MS) in Windows, and it wants to run a chkdsk to search for errors that IT ITSELF may have created in Vista.

Remember that Windows loves to send you through the "Mother May I" game and dance when you close a program .. if one of their poorly written programs or third party abortions hangs up when you close and you select "exit anyway"  that is the message you will get in Vista the next time you boot into it.

---

### Post by Noise... on 2009-04-14
> **oldsoundguy said:**
> that usually means that you did not shut something down PROPERLY (according to MS) in Windows, and it wants to run a chkdsk to search for errors that IT ITSELF may have created in Vista.

So there's no harm in it?

---

### Post by Castor68 on 2009-04-14
Don't worry about those messages. As **oldsounguy** said Vista is trying to check something the Vista did itself.

---

### Post by oldsoundguy on 2009-04-14
Vista is blind to Linux on a disk .. it will see the partition only.  And since the partition is NOT NTFS, it can not scan it.  The only partition that will get scanned is the one with Vista on it.

---

### Post by Noise... on 2009-04-14
> **oldsoundguy said:**
> Vista is blind to Linux on a disk .. it will see the partition only.  And since the partition is NOT NTFS, it can not scan it.  The only partition that will get scanned is the one with Vista on it.

Ah - ok. Thanks a lot. :)

---

### Post by raymondh on 2009-04-14
> **Castor68 said:**
> Don't worry about those messages. As **oldsounguy** said Vista is trying to check something the Vista did itself.

LOLOLOLOLOLOLOL and =D>

---

