---
title: "Help with NTFS partition"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by Tahakki on 2009-12-29
I have a 500GB partition used for storage. I have the following in my fstab for it:

```
/dev/sda3 /media/Storage ntfs user,rw,locale=en_GB.UTF-8,umask=007,uid=1000,gid=46 0 0
```

This means it is mounted at startup, and any user can read/write to it, but it can only be unmounted by root - any way to change this?

Also, if there any way to hide it from the Desktop but keep it in the places menu?

Thanks. :)

---

### Post by lotharmat on 2009-12-29
I may be barking up the wrong tree here but: Could you create a directory somewhere else ie. not /media and mount it there?

afaik that should prevent it from showing up on the desktop but you could add it as a bookmark to show up under places

---

### Post by Tahakki on 2009-12-29
Never mind. I've realised I quite like having it on the desktop. :P

---

### Post by lotharmat on 2009-12-29
did mounting it elsewhere not work then?

---

