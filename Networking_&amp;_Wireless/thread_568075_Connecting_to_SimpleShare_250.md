---
title: "Connecting to SimpleShare 250"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by shaywood on 2007-10-05
Has anyone actually been able to connect to a NAS SimpleShare 250 drive?  I have searched the Internet finding only bits and pieces to help me connect using Ubuntu, but to no avail. I'm certainly a newbe, so it may be my ignorance, but can someone walk me through step-by-step?

---

### Post by shaywood on 2007-10-06
bump

---

### Post by EricDB on 2008-01-30
Kind of an old thread, but in case someone else searches it, here's what has worked for me...I added the following line to my /etc/fstab:

```
192.168.1.102:/shares/SimplePool/NetFolder      /mnt/z        nfs     defaults        0       0
```

Of course you need to mkdir /mnt/z and stick your own SimpleShare's IP address in there.

---

### Post by shaywood on 2008-02-01
Thanks,  I'll give it a try.  I'm new to linux and don't know much about editing files.


Shawn

---

### Post by shaywood on 2008-02-01
It worked !  Thanks!

---

### Post by lilrunninbal232 on 2008-04-02
can somebody please help me with this issue?  I edited the fstab and mounted it but it doesn't find anything when i open the folder.

---

