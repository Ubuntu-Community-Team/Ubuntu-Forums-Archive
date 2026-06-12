---
title: "How do I set up an encrypted install next to a Windows partition?"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by diablo75 on 2009-06-02
Simply put, I'm used to setting up an encrypted LVM with the alternate CD, but only on a fresh HD with no other partitions.  What I want is to have an encrypted linux partition next to a Windows install on the same drive.  Anyone know of a guide for doing this?

---

### Post by unutbu on 2009-06-02
Using the alternate installer CD and select "Manual" partitioning.

You first have to create a clear, unencrypted /boot partition so GRUB can read the boot files.

Similarly, you can create or preserve your Windows partition.

Then you create the new partition and configure it with "Use as: physical volume for encryption". The rest of the process is described here:

[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

Hope this helps. :)

---

