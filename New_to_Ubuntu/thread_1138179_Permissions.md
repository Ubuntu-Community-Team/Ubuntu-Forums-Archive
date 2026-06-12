---
title: "Permissions"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by expatCM on 2009-04-26
I just formatted a drive to change from ext3 to ext4.  No problems.  When I copied all the data back the permissions and groups of everything had changed from user/group to root/root.

How do I reset the user/group?   I have tried with sudo nautilus but this seems a very limited way of changing the user/group.

---

### Post by ddrichardson on 2009-04-26
If you're sure its user:group then```
cd /
sudo chown -R user:group *
```But be sure.

---

### Post by expatCM on 2009-04-26
yep, that did it .....  Thank you :)

---

### Post by ddrichardson on 2009-04-26
You're welcome :-)

Just a thought - if you use tar to archive stuff to move it then permissions are preserved.

---

