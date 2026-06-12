---
title: "new user unable to login"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by saurabh1296 on 2009-05-20
i created a new user sunny.when i tried to login with this username i got an error message your last session lasted for less than 10 seconds when i clicked ok login get terminated and when clicked details it shows can't create /home/sunny/videos etc...please help me

---

### Post by Lampi on 2009-05-20
check the permission of /home using "ls -la /home"

should look sth like this

```
~$ ls -la /home/
drwxr-xr-x  3 root root  4096 2009-04-24 10:29 .
drwxr-xr-x 21 root root  4096 2009-05-12 11:01 ..
drwx---r-x 44 lampi lampi   12288 2009-05-20 08:30
```

---

### Post by ainsworth_t on 2009-05-20
I've seen this error before when there wasn't enough space left on the disk to create the user's home folder and profile. How big is the disk you installed it on?

---

