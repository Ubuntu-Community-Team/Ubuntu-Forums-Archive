---
title: "Disk labels in nautilus"
date: 2009-08-05
forum: New to Ubuntu
---

### Post by m_ad on 2009-08-05
I found [this]("https://help.ubuntu.com/community/RenameUSBDrive") tutorial on how to change disk labels via GParted or the terminal.

My problem - nautilus displays two of my mounted disks (one partition on the internal hard disk and one external) as "XXX GB Media" and not the label.

For example:

```
[matt@matt-desktop:~]$ sudo ntfslabel /dev/sda3
Windows

```

The attached image shows /dev/sda3 in nautilus (highlighted)

My question is, how do I tell nautilus to show the device using it's label?

---

### Post by wojox on 2009-08-05
Unplug it and it may show up. If plugged in it will display the size.

---

### Post by m_ad on 2009-08-05
I'm not sure what you mean..

If I unplug it, the drive doesn't show up in nautilus.

---

