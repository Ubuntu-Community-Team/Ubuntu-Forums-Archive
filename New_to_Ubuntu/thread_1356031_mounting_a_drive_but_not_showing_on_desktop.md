---
title: "mounting a drive but not showing on desktop"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by jmcgovern on 2009-12-15
Is there a way to have a drive automount at startup but not appear on the desktop?  I've used ntfs-config to automount my NTFS partitions but id like them to not appear as icons on my desktop (but accessible through Nautilus).

---

### Post by yeats on 2009-12-15
This will probably help:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by camporter1 on 2009-12-15
This might still work: [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/]("http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/")

Probably easier than modifying fstab or anything else.

---

### Post by fooman on 2009-12-15
open a terminal and type:

```
gconf-editor
```

when the editor opens,  go to apps > nautilus > desktop

then look in the right hand column and uncheck "volumes visible"

hope that helps.

---

