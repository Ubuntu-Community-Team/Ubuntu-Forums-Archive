---
title: "dual boot isues"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by ran1wil on 2009-04-15
I have just decided to lear about linux system and wanted to start with a dual boot with windows xp and ubuntu.xp already installed and i pationed the drive in half and istalled ubuntu on the second part. when i was done i couldnt boot the xp partion
so from inside ubuntu i deleated and reinstalled xp now i can get xp but not ubuntu. when i created the ubuntu partion i merged all my files there and now i cannot load the partion. please help me i want to beable to get my boot loader to access both partions and i dont want to reintall ubuntu. im afraid of loosing my files.

---

### Post by taurus on 2009-04-15
If you reinstalled windows after you've installed Ubuntu, windows will wipe GRUB from MBR so you need to reinstall GRUB to MBR again if you want to boot Ubuntu.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by ran1wil on 2009-04-15
can i reinstall ubuntu with out deleting my files?

---

### Post by taurus on 2009-04-15
It depends where those files located.  Do you have a separate /home partitions?

Usually when you reinstall, you would want to reformat root partition, /, but you don't have to if you don't want to.  The new install will install on top of the previous version.

---

### Post by ran1wil on 2009-04-15
I have attempted to instal grub from the live cd. it said it was successful but when rebuting i didnt get grub just xp again

---

### Post by taurus on 2009-04-15
If you need to access Ubuntu partition, ext3 filesystem, from windows, install fs-driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by ran1wil on 2009-04-15
I will reinstall over the existing ubuntu partition if i wont loose my files. i dont know what are home partitions

---

### Post by taurus on 2009-04-15
Whichever method you want to do, I suggest you _backup_ your personal files first before you dive into it.

---

### Post by ran1wil on 2009-04-15
I would back up but cannot access them on ubuntu. booting the live cd i was unable to find but i know the files are there

---

