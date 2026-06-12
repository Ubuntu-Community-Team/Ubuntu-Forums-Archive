---
title: "Trying to install Ubuntu on a partition"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by mikemamoss on 2011-04-12
Hi, I am trying to install Ubuntu on a partition of my HD, I allocate the space but keep getting error "no root file system" I am not sure which choice from the drop-down menu I should use. thanks.

---

### Post by oldos2er on 2011-04-12
Root file system is /

---

### Post by seawolf167 on 2011-04-12
The easiest way would be to simply have the Ubuntu installer automatically create the necessary mount points, but if you are doing it manually, you'll need to (at the very least) assign two mount points:

/, mounted at /, type ext4
swap, mounted at swap, type swap

Of course you can always create additional partitions for things like /home or /boot.

---

### Post by mikemamoss on 2011-04-12
Thank you it worked.

---

