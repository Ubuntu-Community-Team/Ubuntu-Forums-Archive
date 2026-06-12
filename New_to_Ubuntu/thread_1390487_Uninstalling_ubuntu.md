---
title: "Uninstalling ubuntu"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by 29carriacou on 2010-01-25
Had problems with Gnome desktop. I could only get to see part of it. Tried KDE. Insists on password at startup, but won't accept the one I entered at instalation. I want to uninstall and try again. But how? Can it be done from Windows?

---

### Post by natravis on 2010-01-25
If you want to wipe it out, you can reinstall the same way you did before, just choose to format the Ubuntu related partitions and make sure to keep your windows partition if you so desire.

---

### Post by hhlp on 2010-01-25
reboot with ubuntu cd and installing again but be sure where is your windows partition and your /home partition if you dont' want loose it and use manual partition :

use sudo fdisk -l before that

---

### Post by 29carriacou on 2010-01-25
Thats the problem - I can't. If I try to reinstall, it wants to format a second ubuntu partition alongside the first, leaving the Windows partition intact and little free memory for either of the Ubuntu installations. Am I really dumb, or am I missing something?

---

### Post by J V on 2010-01-25
Choose manually specify partitions ;)

---

### Post by hhlp on 2010-01-25
use your actual ubuntu install in manual partition and format only "/" root partition

---

### Post by halitech on 2010-01-25
why not just reset the password?

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Techsnap on 2010-01-25
> **29carriacou said:**
> Had problems with Gnome desktop. I could only get to see part of it. Tried KDE. Insists on password at startup, but won't accept the one I entered at instalation. I want to uninstall and try again. But how? Can it be done from Windows?

Boot Windows.

Start>Control Panel>Administrative Tools>Computer Management>Disk Management

Find the partition Ubuntu is installed to and delete it, you'll then need to boot your Windows disc and fix the mbr.

Google that part because it's different on both XP and Vista/7 installation media.

---

### Post by dolphinaura on 2010-01-25
boot the ubuntu cd.

go to Applications -> Accessories -> Terminal
type in
```

gparted

```
delete the partition.

---

