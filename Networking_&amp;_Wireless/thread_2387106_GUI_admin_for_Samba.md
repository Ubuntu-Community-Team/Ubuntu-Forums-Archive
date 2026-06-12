---
title: "GUI admin for Samba?"
date: 2018-03-14
forum: Networking &amp; Wireless
---

### Post by oregonbob on 2018-03-14
Does anyone know/use a good GUI for Ubuntu or Xubuntu to manage Samba accounts/shares etc?

I read somewhere that one of the existing Samba GUI's screwed things up. I would just like something reliable.

---

### Post by TheFu on 2018-03-15
If you want reliable samba, don't use GUIs or gvfs. Use either the fstab method or autofs.  No GUI.  The GUIs seem to use gvfs [https://askubuntu.com/questions/194475/slow-gvfs-smb-performance](https://askubuntu.com/questions/194475/slow-gvfs-smb-performance) which seems to be about 3x slower than doing it the manual way. Sometimes being easy trumps better performance, but if you are going to spend the time to setup a permanent connection, it might as well be fast too.

I've seen were people found a GUI to modify the fstab. It seems to use gvfs, which defeats the better performance based on the lines it adds to the fstab.

Sorry, I don't have any good news.  Really, Unix-to-Unix network file sharing should use NFS, not CIFS.

---

### Post by oregonbob on 2018-03-15
I never mentioned mounting Windows filesystems. How will 'fstab method or autofs' help with administering users and shares? It won't.

---

### Post by TheFu on 2018-03-15
> **oregonbob said:**
> I never mentioned mounting Windows filesystems. How will 'fstab method or autofs' help with administering users and shares? It won't.

You are correct.

Sorry oregonbob.  I saw this message yesterday and specifically didn't reply hoping that someone else would. Upon seeing it again, I didn't re-read it carefully and was stuck thinking about remote CIFS mounts, not providing a service to other systems.

Of course, none of that helps you get an acceptable answer.  I apologize.

---

### Post by Habitual on 2018-03-16
[https://www.samba.org/samba/docs/old/Samba3-HOWTO/SWAT.html](https://www.samba.org/samba/docs/old/Samba3-HOWTO/SWAT.html)

---

