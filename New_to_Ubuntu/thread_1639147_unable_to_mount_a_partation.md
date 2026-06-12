---
title: "unable to mount a partation"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by bj218 on 2010-12-06
I guess I loused up something when I closed a partition!! Can someone 
tell me how I can get it back? I hope the attached picture is enough to
explain my problem!!

---

### Post by TeoBigusGeekus on 2010-12-06
Try 
```
mount /dev/sdc6 /media/homeu
```

---

### Post by bj218 on 2010-12-06
> **TeoBigusGeekus said:**
> Try 
```
mount /dev/sdc6 /media/homeu
```

I think this would work but apparently I have a bigger problem! From the
attached picture terminal says There is no homeu but I do or did have a homeu before I closed it a day ago. Is there any thing more I can do to recover my data or get this partition back?

---

### Post by bodhi.zazen on 2010-12-06
> **bj218 said:**
> I think this would work but apparently I have a bigger problem! From the
attached picture terminal says There is no homeu but I do or did have a homeu before I closed it a day ago. Is there any thing more I can do to recover my data or get this partition back?

```
sudo mkdir /media/homeu
```

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by bj218 on 2010-12-07
> **bodhi.zazen said:**
> ```
sudo mkdir /media/homeu
```

See also:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

Thanks to all I got everything back.

---

