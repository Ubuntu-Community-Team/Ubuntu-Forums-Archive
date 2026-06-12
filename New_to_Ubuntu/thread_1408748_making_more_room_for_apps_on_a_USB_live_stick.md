---
title: "making more room for apps on a USB live stick"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by bholtby on 2010-02-16
I have an installation of Xubuntu 9.1 on a 16gB stick. The "file system" is where apps appear to be installed and it is 4gB in size. The "USB Startup Disk Creator" allowed me to reserve a maximum of 4 gB for saving things. I don't know if the two limitations are related. How can I expand the "file system" up to the size of the stick? The file/directory structure is opaque to a windows and mac user. Is there a simple explanation of what is what on a live USB installation?

Thanks

---

### Post by bholtby on 2010-02-17
Well Duh. After reading some more about Ubuntu on a USB stick at Pendrivelinux, it became clear that 4 gB is the file size limit for a disk formatted as FAT32. The linux file system is stored as an ext2 formatted virtual drive within a single FAT32 file - hence the limitation.

---

