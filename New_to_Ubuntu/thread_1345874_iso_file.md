---
title: "iso file"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Drenriza on 2009-12-04
How can i make an iso file of en existing cd i already have in ubuntu?.

hope someone can help me.
Thanks on advance:KS

Kind Regards

---

### Post by whoop on 2009-12-04
[http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/ubuntu_how_to_create_iso_image_from_cd_dvd/)

---

### Post by jbrown96 on 2009-12-04
It's worth noting that you may have trouble using /dev/scd0. Usually it's not an issue, because the overwhelming majority of computers will list the cd drive as /dev/scd0, but it is possible that this can cause a problem. It's usually safer to use /dev/cdrom, which is a link to the actual device (usually /dev/scd0)

use ```
cat /dev/cdrom > ./file.iso
```

---

### Post by Drenriza on 2009-12-04
Thanks guys.

[http://www.tech-recipes.com/rx/2769/...e_from_cd_dvd/](http://www.tech-recipes.com/rx/2769/...e_from_cd_dvd/)

is working without a hitch (i think:KS)

arnt their someway you can see a process counter to when it is done?.

---

### Post by jbrown96 on 2009-12-04
Not from the command line. Brasero (available somewhere in the Applications menu) can also rip isos. It's much friendier and will give you a progress bar.

---

### Post by Drenriza on 2009-12-04
Hows does that work, ive been in the program but codent find an iso rip option.

---

### Post by jbrown96 on 2009-12-04
In Brasero-->Disk Copy, then "select a disk to write to" choose image file.

---

