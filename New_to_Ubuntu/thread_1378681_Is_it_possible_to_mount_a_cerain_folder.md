---
title: "Is it possible to mount a cerain folder"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by Kedster on 2010-01-11
Hey every one 
alright 

So i would like to know if there is a way to use fstab to mount a folder on another partition to a mount point. there is a folder on another partition called music and i want to mount as /Home/ketterer/Music

---

### Post by sisco311 on 2010-01-11
Add something like 
```
/path/to/Music    /home/ketterer/Music    auto    bind
```
to the fstab, then run:
```
sudo mount -a
```

---

### Post by Kedster on 2010-01-11
Ok ill try that, Quick Question, Will this also work on mac osx there is an fstab for the same purpose

---

