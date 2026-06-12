---
title: "Resizing Partition"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-10-24
Hello again!

I just finished installing Ubuntu and getting my Internet set up, and now I would like to remove Windows XP and increase Ubuntu's partition size.

I booted up into the Ubuntu Live CD, and ran gparted. I deleted the windows partition, and clicked on resize/move to increase Ubuntu's partition. However, it would not let me drag the partition farther into the unallocated space.

Any Suggestions?
Thanks in advance!

---

### Post by bumanie on 2009-10-24
You have probably installed ubuntu into a logical partition. If so, it will be encased in a blue box on the gparted gui. You can increase the size of the blue box and then increase ubuntu. You will have to reinstall grub as well after altering the partitions.

---

### Post by jnorthr on 2009-10-24
might also be that the format  used by the windows partition is not the same as  you  used for the ubuntu partition, so you would be unable to expand a 'logical' partition across differing formats.

consider just wiping the windows and using that partition to store music, photos, etc

---

### Post by darkeye123 on 2009-10-24
Thanks a lot!

Turns out it was a logical partition and I need to drag that across first.
Thanks again :)

---

