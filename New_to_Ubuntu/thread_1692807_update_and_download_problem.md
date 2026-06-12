---
title: "update and download problem"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-02-22
I am not able to update or download any software. Everytime it shows this problem!! can I do anything???

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by tjwoosta on 2011-02-22
it looks like your package manager is already running. (you can only have one instance at a time)

---

### Post by amitpokhrel on 2011-02-22
no none of my pakage manager is runnung. I tried to update immediately after i restarted my system.

---

### Post by tjwoosta on 2011-02-22
In that case you proabably have a left over lock file in /var/lib/dpgk from sometime when the process was interupted.

Navigate to that directory
```
cd /var/lib/dpkg
```

list the files
```
ls
```

If a file named "lock" is present remove it (you need to have super user privelages to remove it since its a system file)
```
sudo rm lock
```

---

### Post by sikander3786 on 2011-02-22
Or just a simple reboot might do the trick.

---

### Post by tjwoosta on 2011-02-22
> **sikander3786 said:**
> Or just a simple reboot might do the trick.

I assumed this meant he already did ;)
> no none of my pakage manager is runnung. I tried to update immediately after i restarted my system.

---

### Post by amitpokhrel on 2011-02-23
> **tjwoosta said:**
> In that case you proabably have a left over lock file in /var/lib/dpgk from sometime when the process was interupted.

Navigate to that directory
```
cd /var/lib/dpgk
```



is it dpgk or dpkg???

---

### Post by tjwoosta on 2011-02-23
> **amitpokhrel said:**
> is it dpgk or dpkg???

yea, sorry, typo, its dpkg  (stands for debian package)

---

### Post by arpanaut on 2011-02-23
> **tjwoosta said:**
> yea, sorry, typo, its dpkg  (stands for debian package)

So change it in your original post to avoid the confusion.
thanks

---

