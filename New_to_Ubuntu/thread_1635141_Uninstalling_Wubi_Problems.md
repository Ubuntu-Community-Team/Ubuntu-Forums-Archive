---
title: "Uninstalling Wubi Problems"
date: 2010-12-01
forum: New to Ubuntu
---

### Post by Devio on 2010-12-01
Hi there, I've made uninstalling Wubi and installing the full version of Ubuntu...

In preparation of a change of operating systems I updated from Windows Vista32 to Windows 7 64, this kept some old files in a Windows.old folder but outside was the 'ubuntu' folder for Wubi, inside was the uninstaller.  Unfortunately the uninstaller doesn't actually work anymore.

Is there another way to uninstall Wubi?

---

### Post by bcbc on 2010-12-01
Delete c:\wubildr*
Delete c:\ubuntu
If there is still a boot entry for Ubuntu at startup use bcdedit (look for instruction on Microsoft website) or a tool called easyBCD.
Delete any registry entries referring to Ubuntu or Wubi

Any data you had on Ubuntu will be lost. If you need to get data off it, download ext2read ([http://ext2read.blogspot.com/](http://ext2read.blogspot.com/)) and point it at c:\ubuntu\disks\root.disk

---

