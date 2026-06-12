---
title: "Cannot mount CD/DVD drive"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by capinlarry on 2009-08-24
I just installed Ubuntu on a Dell desktop and the DVD/CD rom drive does not mount. Neither appear under PLACES>COMPUTER and nothing happens when i insert a CD or DVD in either drive. Any ideas?

---

### Post by zkriesse on 2009-08-24
I had that problem. Did you check the cd drive for errors? Obviously you have access to another pc..

---

### Post by capinlarry on 2009-08-26
yes i did, the strange thing is that i had this problem with fedora 11 as well, maybe a compatibility issue?

---

### Post by bumanie on 2009-08-26
Are the drives registered in fstab? Post the output of terminal command > cat /etc/fstab

---

### Post by fanglinyong on 2009-08-26
have you use command like this :
```
mount
```

---

### Post by MrWES on 2009-08-26
> **capinlarry said:**
> I just installed Ubuntu on a Dell desktop and the DVD/CD rom drive does not mount. Neither appear under PLACES>COMPUTER and nothing happens when i insert a CD or DVD in either drive. Any ideas?

Place the DVD/CD in the drive and close. Wait a few seconds and then check the system log for error messages:

```
dmesg | more
```


look towards the end of the message log. Post, if any, error messages.

Bill

---

### Post by capinlarry on 2009-08-26
> **MrWES said:**
> Place the DVD/CD in the drive and close. Wait a few seconds and then check the system log for error messages:
 
```
dmesg | more
```
 
 
look towards the end of the message log. Post, if any, error messages.
 
Bill
 
 
the only error message i see is ata2: SRST failed (errno=-16)

---

### Post by capinlarry on 2009-08-26
> **bumanie said:**
> Are the drives registered in fstab? Post the output of terminal command
 
I get "No such file or directory"

---

