---
title: "Can Not Unmount CD Drives in Lucid"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by Quantum_Mechanic on 2010-05-29
I have both Karmic and Lucid in a dual boot system. I am able to mount/unmount/read/write/copy and burn CDs in Karmic using K3d with no problems. In Lucid, when I load a CD, it shows up on the desktop and I can see the files on it. When I right click on the icon, unmount does not even show up as an option. Not even greyed out. Cut, copy, etc. are all greyed out. When I try to unmount in K3d I get an unmount error message. Is this some kind of permissions issue???

---

### Post by Quantum_Mechanic on 2010-05-29
Well, I did a little more digging and found that the lack of an unmount command when you right click the CD Icon is a "feature" in Lucid. You can right click and eject but not unmount. If you need to burn a disk you must run```
 umount /dev/sr0
``` or what ever your CD or DVD device is before you can burn. Seems like something was lost between 9.10 and 10.04.

---

