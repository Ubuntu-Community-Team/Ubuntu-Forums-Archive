---
title: "hard drive owned by root after formating w gparted"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by e1ektrob0y on 2010-03-01
As the title says, I formatted my second hard disk with gparted and now i cant create folders or anything as it is now owned by root. How can i change the permissions or owner? I want to use it as a back up drive so i formatted it to ext3 using gparted...thanks :)

---

### Post by hemimaniac on 2010-03-01
Is there an post in your /etc/fstab for it, if not i suggest installing pysdm (Storage manager) and set the drive to defaults and apply, it will auto mount with read/write for all on restart

---

### Post by e1ektrob0y on 2010-03-01
Is there not a way to just reformat with gparted but have the drive read/write for all?

---

### Post by johngreth on 2010-03-01
You should be able to mount the drive as long as you have an admin password, but if not, try typing
```
gksudo nautilus
```
to access a file browser with root permissions. Then mount the drive.

As far as permissions, it's always been my experience that the drive will have the permissions of whichever user mounted it.

---

### Post by e1ektrob0y on 2010-03-02
thanks. solved...

---

### Post by hansheijmans on 2010-03-02
Or set the right permissions on your mount point..., e.g.
```
sudo chown *user:user */mnt/mysecondharddisk
```

---

### Post by johngreth on 2010-03-02
I'm glad you brought that up, hansheijmans. I thought doing something with chown might be better, but I wasn't sure what location to run it on (media, mnt, dev...). I also thought about the possibility of using chmod to set all permissions, but I didn't know what security risks went along with that. Could you offer more advice about chmod and security risks for future reference?

---

