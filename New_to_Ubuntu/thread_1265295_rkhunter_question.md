---
title: "rkhunter question"
date: 2009-09-13
forum: New to Ubuntu
---

### Post by heyyy on 2009-09-13
i did a check with rkhunter and in the log file i had the following:
```
...
[15:11:05] /usr/sbin/unhide                                  [ Warning ]
[15:11:05] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[15:11:05] /usr/sbin/useradd                                 [ OK ]
[15:11:05] /usr/sbin/userdel                                 [ OK ]
[15:11:05] /usr/sbin/usermod                                 [ OK ]
[15:11:05] /usr/sbin/vipw                                    [ OK ]
[15:11:05] /usr/sbin/unhide-linux26                          [ Warning ]
[15:11:05] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
...
```

so what does it mean?

---

### Post by zhanglini on 2009-09-13
Correct me if I am wrong, I think that is actually a rkhunter error --- it is a part of rkhunter.

---

### Post by heyyy on 2009-09-13
> **zhanglini said:**
> Correct me if I am wrong, I think that is actually a rkhunter error --- it is a part of rkhunter.

maybe your right
im new to linux world so im not sure

---

### Post by Screwdriver0815 on 2009-09-13
you must update the "evil-good"-database in rkhunter

```
sudo rkhunter --propupd --update 
```

then normally you should not get this message again and it is able to search for newer rootkits too

---

### Post by heyyy on 2009-09-13
> **Screwdriver0815 said:**
> you must update the "evil-good"-database in rkhunter

```
sudo rkhunter --propupd --update 
```

then normally you should not get this message again and it is able to search for newer rootkits too

ive already done that but still the same message

---

