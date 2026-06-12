---
title: "Does installing Ubuntu through Wubi mean that Ubuntu is working under Windows?"
date: 2011-05-21
forum: New to Ubuntu
---

### Post by snigam3112 on 2011-05-21
When I start my computer, I get two boot screens, the first being Windows Boot Manager and other being Ubuntu's - does this mean that Ubuntu functioning as an independent OS without having anything to with Windows or is it first booting into Windows and then into Ubuntu?

If it is booting into Windows first, how do i make Ubuntu independent of it?

---

### Post by jtarin on 2011-05-21
[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29)

To make independent...uninstall WUBI and the install Ubuntu on its own partition.

---

### Post by bcbc on 2011-05-21
> **snigam3112 said:**
> When I start my computer, I get two boot screens, the first being Windows Boot Manager and other being Ubuntu's - does this mean that Ubuntu functioning as an independent OS without having anything to with Windows or is it first booting into Windows and then into Ubuntu?

If it is booting into Windows first, how do i make Ubuntu independent of it?

It's booting independently from Windows. But it is using a virtual disk that resides on the Windows file system (ntfs or fat32). It is not as robust as a direct install with a dedicated partition and it is also a bit slower than a direct install.

You can either [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") a wubi install to a direct install, or uninstall (from windows control panel, add/remove programs) and reinstall direct (just backup any data before uninstalling because the Ubuntu install will be deleted.)

---

### Post by dFlyer on 2011-05-21
> **snigam3112 said:**
> When I start my computer, I get two boot screens, the first being Windows Boot Manager and other being Ubuntu's - does this mean that Ubuntu functioning as an independent OS without having anything to with Windows or is it first booting into Windows and then into Ubuntu?

If it is booting into Windows first, how do i make Ubuntu independent of it?

If your using wubi then your running ubuntu as a window program. My advice is to remove wubi and dual boot until your ready to dump windows.

---

### Post by bcbc on 2011-05-21
> **dFlyer said:**
> If your using wubi then your running ubuntu as a window program. My advice is to remove wubi and dual boot until your ready to dump windows.

No that's not correct. Wubi (the installer) is a windows program. You can install and uninstall Ubuntu from Windows, but Ubuntu does not run as a windows program.

---

