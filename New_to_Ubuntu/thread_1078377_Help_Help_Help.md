---
title: "Help Help Help"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by tychotma on 2009-02-23
Hughs - I think I did anything wrong - anyway how could it be - that my mad machine - ubuntu hardyheron804 - denies access to my desktop, storedevice even the personal folder - its not connected (german: keine Vorgabeaktion verknüpft) where is the trick?? 
It started as i tried to communicate with my printer...

---

### Post by Jeroen Vernooij on 2009-02-23
Wait a second -- you aren't permitted to access your personal home folder? How can you login then??

try 
```
sudo chown -R **USERNAME FOLDER**
```
(replace **USERNAME** with your username and **FOLDER** with the path to the folder you can't access, for example /media/disk-1)

---

