---
title: "samba help"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by Dave.B on 2011-03-16
I have samba installed and am  trying to edit smb.conf with gedit.

i am trying to edit and it will not let me type anything in.

thanks for the help

Dave

---

### Post by VastOne on 2011-03-16
> **Dave.B said:**
> I have samba installed and am  trying to edit smb.conf with gedit.

i am trying to edit and it will not let me type anything in.

thanks for the help

Dave

You must open it via sudo to be able to edit it

sudo gedit /path/to/smb.conf

---

### Post by PunkLV on 2011-03-16
Make a copy of the original smb.conf as well
```
sudo cp /etc/samba/smb.conf ~/.smb.conf.original
```

---

### Post by Dave.B on 2011-03-16
DOH 

forgot about old mr SUDO

---

