---
title: "Network sharing"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by Yoshi_ on 2009-12-31
Hello,

It may be possible that this question has been asked a frequent times...
But I want to know sure, when if I instal Ubuntu on my laptop - wich has the shared folders - that it will still be possible to acces these shared folders with an machine with OS Windows Vista/Xp

And if possible, could someone give me some information or a link with a tutorial about folder sharing in Ubuntu.

Thanks, Yoshi

---

### Post by jbrown96 on 2009-12-31
It's certainly possible to share your files from Windows to Ubuntu.

There are two methods to install Ubuntu. The first is called Wubi, where you install Ubuntu like a program within Windows. One of my friends recently did this, and it was very easy. Furthermore, all the files from Windows automatically showed up in Ubuntu. The only drawback is if you want to get rid of Windows, then you will need to reinstall Ubuntu.
The second method is to do a dual-boot. Just burn Ubuntu to a CD, then boot from it. The installer can automatically do the partitioning, so you won't have to mess with that. After you install and reboot. The "Places" menu at the top should have an entry for your Windows partition. It will likely be identified by its size.

---

### Post by avtolle on 2009-12-31
If I understand the question, the OP wants to be sure the files may be shared over a network with a Windows machine. Yes, they may. Samba will need to be installed on the Ubuntu machine and configured. [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) gives information.

---

### Post by Morbius1 on 2009-12-31
There's actually two different ways to share folders in linux: Classic Samba and Nautilus-share. For most users nautilus-share should be enough. With all due respect to the developers of nautilus-share, it's very Windows like:

Open Nautilus > Right click on a folder in your /home directory > Select "Sharing Options" > Check off all the boxes > Select "Create Share".

 It can get more complicated than that depending on whether you want to require authentication and what it is you're sharing, but that's the basic HowTo on nautilus-share.

---

