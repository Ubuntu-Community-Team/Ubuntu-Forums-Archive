---
title: "Removing Network Mounted Folders from the Desktop"
date: 2008-07-16
forum: Networking &amp; Wireless
---

### Post by ke3ju on 2008-07-16
After upgrading from Gutsy to Hardy, all of the network share folders that are mounted from fstab on login, appear on my desktop.  I have searched high and low, and can not find a way to stop this from happening.

Just to clarify, the actual mount points are not the desktop, they are in the Network folder in my home directory.  I only want them to appear in the Network folder, and not on the Desktop.

Does anyone know a way to circumvent this action?

Best Regards,
Ed

---

### Post by Iowan on 2008-07-16
Does deleting the icon mess up the mount (CAN you delete the icon?)

---

### Post by mb_webguy on 2008-07-16
Here's how to remove network folders from the desktop:

1. In the terminal, type gconf-editor.

2. Navigate to apps->nautilus->desktop and uncheck volumes_visible.

3. ???

4. Profit!!!


EDIT:  I just noticed that this removes *everything* from the desktop, including things like locally mounted drives, but it *does*, nonetheless, remove those pesky network volumes.

---

### Post by ke3ju on 2008-07-16
It worked perfectly...thank you so much for the help...

Best Regards,
Ed

---

