---
title: "Unmount drive fail"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by newbeeman on 2009-12-12
During the upgrade to 9.1 I lost the connection to my Win drive.
I installed NTFS config and made a connection to both an external drive and the Win drive.
Now I cannot unmount the Win drive.
The error reads
"Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /media/100GB"
Can anyone sort me out, please.

---

### Post by newbeeman on 2009-12-12
Bump

---

### Post by newbeeman on 2009-12-12
Bump

---

### Post by ~sHyLoCk~ on 2009-12-12
So use:

```
sudo umount /dev/sda1
```

---

### Post by abeisgreat on 2009-12-12
> **newbeeman said:**
> During the upgrade to 9.1 I lost the connection to my Win drive.
I installed NTFS config and made a connection to both an external drive and the Win drive.
Now I cannot unmount the Win drive.
The error reads
"Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /media/100GB"
Can anyone sort me out, please.

My guess would be that you are trying to unmount the drive without root privileges. Try running the command
```

sudo umount /media/100GB

```
from a terminal. Should work ;)

P.S. Shylock beat me to it.

---

### Post by newbeeman on 2009-12-12
> **abeisgreat said:**
> My guess would be that you are trying to unmount the drive without root privileges. Try running the command
```

sudo umount /media/100GB

```
from a terminal. Should work ;)

P.S. Shylock beat me to it.
Tried both messages got a "Command not found" in both cases.

---

### Post by abeisgreat on 2009-12-12
> **newbeeman said:**
> Tried both messages got a "Command not found" in both cases.

I can't imagine that program not being there. Are you sure you're typing it 100% correct? Note that it is umount not unmount.

---

### Post by newbeeman on 2009-12-12
> **abeisgreat said:**
> I can't imagine that program not being there. Are you sure you're typing it 100% correct? Note that it is umount not unmount.

My Bad. Shylock had the answer.
Thanks.

---

