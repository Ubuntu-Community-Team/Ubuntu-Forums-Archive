---
title: "Can't view HDD contents!"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by Nikhil_07n on 2009-10-07
I'm unable to view the partition's original contents in which I have just installed ubuntu through wubi.

It's not even showing up in the file browser.

---

### Post by BQAggie2006 on 2009-10-07
That's because Wubi doesn't install Ubuntu in a true disk partition, but within a virtual disk file created within the Windows file system. Therefore, the only filesystem and partitions you will be able to access are those located within the Wubi Ubuntu installation.

To get back to your Windows files, just reboot your computer and boot into Windows instead of Ubuntu.

---

