---
title: "How to mount Windows share"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by wrgb2 on 2009-11-12
Hi,

How do I have Ubuntu automatically mount a Windows network shared folder on startup?  I currently have to browse to Places > Network and open the folder each time I want to mount it.

---

### Post by phillw on 2009-11-12
> **wrgb2 said:**
> Hi,

How do I have Ubuntu automatically mount a Windows network shared folder on startup?  I currently have to browse to Places > Network and open the folder each time I want to mount it.

System --> Administration --> Disk Utility   should take you the option to auto-mount

Regards,

Phill.

---

### Post by longtom on 2009-11-12
Make a sub directory in your /media directory (let's call it filename).


Add this to your fstab file:

```

//computername/filename /media/filename cifs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode,umask=000 0 0

```

once done do

```

sudo mount -a

```

Good luck.

---

