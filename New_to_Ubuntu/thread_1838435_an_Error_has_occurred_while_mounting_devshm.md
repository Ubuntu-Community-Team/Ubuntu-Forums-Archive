---
title: "an Error has occurred while mounting /dev/shm"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by nastynate1219 on 2011-09-03
I need help when I start up my computer i get this message
 
an Error has occurred while mounting /dev/shm
 
and it asks me if i want to press "S" to skip mounting or "M" for manuel recovery
 
but when I go with M it bring me onto my desktop as normal 
 
But I cant get google to work or my email
 
 
WHAT DO I DO CAN SOMEONE HELP ME PLEASE???????????????????????

---

### Post by nastynate1219 on 2011-09-05
solved by actionparsnip (andrew-woodhead666) said on 2011-09-04: #1
Run:
gksudo gedit /etc/fstab

add this line:
tmpfs /dev/shm tmpfs defaults 0 0

Save the new file, close gedit and run:
sudo mount -a

Should be ok

---

