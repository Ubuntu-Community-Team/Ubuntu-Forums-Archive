---
title: "Question about a Hard Drive with Ubuntu"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by TAspr on 2011-05-23
Hello, I installed Ubuntu on a secondary hard drive running Windows7 and Ubuntu.  Is there any reason why the secondary drive will not show up in Windows7?  I can boot to it fine through the Grub menu.

---

### Post by Grenage on 2011-05-23
Most likely because it's using a filesystem that Windows does not support - ext4.  It will most likely show up under *control panel/administrative tools/computer management*, or whatever the W7 equivalent.

---

### Post by nothingspecial on 2011-05-23
Probably because windows cannot read linux filesystems.

---

### Post by elliotbeken on 2011-05-25
Right click "My Computer" and select "Manage then disk management"

---

### Post by TAspr on 2011-05-25
> **elliotbeken said:**
> Right click "My Computer" and select "Manage then disk management"
 
And then?

---

### Post by Grenage on 2011-05-25
> **TAspr said:**
> And then?

You'll be able to see your discs...

You won't be able to actually access the data; as has already been said, Windows cannot read ext4 partitions.

---

