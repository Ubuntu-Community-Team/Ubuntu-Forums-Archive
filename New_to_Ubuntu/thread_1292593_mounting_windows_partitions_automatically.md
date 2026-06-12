---
title: "mounting windows partitions automatically"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by AliSajidImami on 2009-10-16
Hello everyone, i was wondering if i can mount my windows partitions automatically. I tried that by going to startup applications and thenwriting a new one. In the Command field i entered the terminal command for it. but it doesnt work when normally on the terminal it works.

---

### Post by abhishek.malhotra35 on 2009-10-16
Add the mount entries in /etc/fstab. Reboot the system. Your partitions will get mounted on startup.

---

### Post by arrange on 2009-10-16
Check out [ntfs-config]("http://flomertens.free.fr/ntfs-config/"). It should edit the *fstab* file automatically for you and after reboot you will see the partition mounted read-write.

---

### Post by AliSajidImami on 2009-10-16
Thanks for everything guys. :-)

---

