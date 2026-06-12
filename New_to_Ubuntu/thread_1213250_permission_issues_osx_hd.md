---
title: "permission issues osx hd"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by nef919 on 2009-07-14
Hello all. I had my powerbook run over by a car while chasing the guy the snatched it some time ago. I have some info on the drive which is ok but am unable to access. I have placed the drive in a usb enclosure and mounted it on my Jaunty machine, but keep getting a permissions error when I try to view anything in my home folder on the drive. Any way to get at the info?

---

### Post by Bölvaður on 2009-07-14
you will need to run as a super user.

alt+f2

type: gksu nautilus

try again now.

make sure to give your self the permissions to access the files after you have moved them to your computer.

---

### Post by LewRockwell on 2009-07-14
```
gksudo nautilus
```

that's what I would try first

.

---

### Post by nef919 on 2009-07-14
Thanks guys that did it. Glad I asked as I thought it had something to do with uid not matching. I know osx starts at 500 and I know my uid is 1002 on the ubuntu box. Again thanks.

---

