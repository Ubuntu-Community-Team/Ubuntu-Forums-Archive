---
title: "installation help with ubuntu"
date: 2010-12-15
forum: New to Ubuntu
---

### Post by hunter99507 on 2010-12-15
I just reinstalled ubuntu and i forgot what program i need to install.  I have a NAS that has windows media connect 2.0 on it and also shows up as a wireless drive.  I cant remember what i installed last time to see it under network, but as of now i cant see it.  Any suggestions?

---

### Post by papibe on 2010-12-15
If you were sharing files from Ubuntu to Windows machines, you were probably using samba. To install it look for samba on the Software Center, or try this:
```
$ sudo ap-get install samba
```
Regards.

---

### Post by hunter99507 on 2010-12-15
So i got samba to work and it shows my drive I was looking for but now it wont let me open it.  I get the error message :Failed to mount Windows share. How do i get past that?

---

### Post by hunter99507 on 2010-12-15
I just restarted my computer again and now i cant open my iomega drive anymore. I get this error message when i try to open iomega. "Failed to retrieve share list from server"

---

### Post by papibe on 2010-12-16
Are you using Ubuntu server or the desktop version?

---

