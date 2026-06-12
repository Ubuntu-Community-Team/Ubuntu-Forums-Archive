---
title: "When on partitioning while installing, what do i need to set the new partition as?"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by random turnip on 2009-07-04
I've gotten to the "prepare partitions" bit, sda5 is now the new ubuntu (i formatted the old ubuntu one), do i keep the "use as" box as "swap area" and make it to the size that i want?

Ok, it won't let me have any more than 2928MB for the new "swap area", what do i need to do to make the new Ubuntu partion fill the 63GB empty space?

---

### Post by 73ckn797 on 2009-07-04
If you are wanting to make the remaining space into the Ubuntu partition you will need to use Gparted from the LiveCD. Right click on the section you want to change, unmount it if it is mounted, then delete or format that part to ext3.

---

