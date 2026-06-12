---
title: "How do you resize/create partitions??"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by JamesParnell on 2009-10-13
i no longer have the installer on my usb stick, and i want to increase my partition size without using the installer

---

### Post by mhgsys on 2009-10-13
open up a terminal ; 

typ;

```

sudo apt-get install gparted

```

then go to System> Administration > Partition editor
Or typ 
```

 gksudo gparted

``` 
in terminal

---

### Post by JamesParnell on 2009-10-13
i dont have internet on my netbook (ubuntu installed) yet, is there a package i can download via windows onto a flash disk?? im running 9.04 jaunty

---

### Post by jimingkui on 2009-10-13
Gparted,good partition editor!

---

### Post by jimingkui on 2009-10-13
[http://gparted.sourceforge.net/index.php]("http://gparted.sourceforge.net/index.php")

---

### Post by JamesParnell on 2009-10-13
thanks for that

---

### Post by JamesParnell on 2009-10-13
loaded the iso onto the disk using unetbootin, but it doesnt work....what do i do to install it??

---

### Post by Paqman on 2009-10-13
> **JamesParnell said:**
> loaded the iso onto the disk using unetbootin, but it doesnt work....what do i do to install it??

The normal LiveCD version of the Gparted disk won't work, you'll need to get the [LiveUSB version]("http://gparted.sourceforge.net/liveusb.php"), or else just create another Ubuntu LiveUSB, since that has Gparted on it as well.

---

### Post by JamesParnell on 2009-10-13
could this be more annoying...how do i find the device name.....??

---

### Post by carml on 2009-10-13
Try to type oon a terminal ```
df -h
```and press return.

---

