---
title: "Removing mount icon from desktop"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by johnharris85 on 2010-04-10
I have mounted a windows drive with my music on it to my home/john/music folder but it has put an icon on the desktop for the mounted 'Music' drive. I thought it only put drives mounted to /media/ on the desktop. Is there anyway to remove this without losing my other mounted drives and usb devices (by going through gconf-editor)?

Thanks, 

John

---

### Post by themusicalduck on 2010-04-10
In gconf-editor, go to apps > nautilus > desktop and uncheck volumes_visible.

---

### Post by johnharris85 on 2010-04-10
> **johnharris85 said:**
> Is there anyway to remove this without losing my other mounted drives and usb devices (by going through gconf-editor)?

Doing that removes ALL mounted drives. I don't want to do that.

---

### Post by 2hot6ft2 on 2010-04-10
unmount it and it should go away. To still have it mounted and not visible while the rest are, not that I know of. All or nothing.

---

