---
title: "Setting file/folder permissions"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by donescamillo on 2010-05-20
Hi,

I am running 9.10.I have a NTFS partition which get mounted at boot time automatically (having configured it with NTFS config).
I want to set permissions for folders in this partition. From a sudoer user I run in terminal: gksu nautilus, right-click on a folder and go to the permissions tab.
There the Owner and Group drop-down boxes are set to root. I imagine it works like this: I select a group in the group box and then I select the desired access for this group and so on for every group that I want to change permissions. The problem is that when I change the Group drop-down entry from root to anything else it goes back to root immediately.
Am I doing something wrong?

regards,
don escamillo

---

### Post by jlaki on 2010-05-20
sudo chown -R username:username path

---

### Post by Ozymandias_117 on 2010-05-20
> **jlaki said:**
> sudo chown -R username:username path

sudo chown -R username:**groupname** path

eg. ```
 sudo chown -R Ozymandias:Admin /mnt/my_mount/stuff/
```

---

### Post by oldos2er on 2010-05-20
chown won't work on an NTFS partition. You'll need to set the permissions you want in /etc/fstab, see [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by donescamillo on 2010-05-21
Hi,

thanks for your replies. I am sure I can do this from terminal, but I was wondering why I could not do it from Nautilus. Apart from being easier it seems safer as there is no danger of mistyping.

regards,
donescamillo

---

