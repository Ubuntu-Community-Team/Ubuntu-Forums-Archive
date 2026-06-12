---
title: "Upgrade problem"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by Dr. div11 on 2011-05-07
now i am trying to update the last few packages...
 this is what the errors are..

dragon11@Dark-Oblivion:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups evolution-plugins
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
..


please tell me what do i do...!!

---

### Post by jramshu on 2011-05-07
More info is needed. What version are you running?

EDIT: Sorry, I see 11.04 listed in your profile there.
Did you upgrade from 10.10 to 11.04?

---

### Post by Dr. div11 on 2011-05-07
> **jramshu said:**
> More info is needed. What version are you running?

EDIT: Sorry, I see 11.04 listed in your profile there.
Did you upgrade from 10.10 to 11.04?


oh sorry no i am not running 11.04 ..m running ubuntu 10.10.. please tell me what more info do u need...

---

### Post by jramshu on 2011-05-07
Try this:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Sorry if sometimes I reply a little slow, I am all over the place on here. LOL

---

