---
title: "Accessing second hard drive with SAMBA"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by ChrisRChamberlain on 2010-07-02
Hi all

Have a PC with 2 hard drives with Ubuntu Server 10.04 LTS installed on each drive, drive selection enabled on startup through GRUB.

SAMBA is installed on both OS and would like Windows to access the drive _not_ running Ubuntu.

What would be the path statement in /etc/samba/smb.conf and does the drive need to be mounted prior to accessing it?

TIA

Chris

---

### Post by ChrisRChamberlain on 2010-07-02
Eventually found a working solution, mount the second drive in a folder of the first drive

```
sudo lvdisplay
```
... and get the LV Name, ie /dev/servername/root

```
sudo mount /dev/servername/root/ /foldername/foldername
```
... to mount the second drive


If needed...

```
sudo umount /dev/servername/root /foldername/foldername
```
... to unmount the second drive

---

