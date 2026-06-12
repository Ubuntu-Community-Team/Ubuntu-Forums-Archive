---
title: "Formating Usb To Ntfs Through Ubuntu 10.04?"
date: 2010-11-22
forum: New to Ubuntu
---

### Post by WhatAreHackers on 2010-11-22
Basicly the title above.

---

### Post by spikoley on 2010-11-22
Gparted works great and is easy to use.  Just make sure you select the right drive in the upper right hand corner.

```
sudo gparted
```

if its not installed by default then run:
```
sudo apt-get install gparted
```

or use this link:
[apt://gparted]("apt://gparted")

---

### Post by BrandonC19 on 2010-11-22
GParted is a bit much (read: OVERKILL) for this task....


It's easier to just go to System -> Administration -> Disk Utility, then select your USB device on the the left, and use the pane on the right to format it.

---

