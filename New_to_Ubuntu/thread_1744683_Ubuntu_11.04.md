---
title: "Ubuntu 11.04"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by jrev on 2011-04-30
I just installed the Ubuntu 11.04 on the same hard disk as the ubuntu 10.04
There is no sound on the PC..
What shall I do ? 
I cannot read any CD with Banshee.
There is no sound in the videos on the Net 
the alarm is "cannot read the track " or something similar :P
Any clue ?

---

### Post by lidex on 2011-04-30
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**

---

### Post by jrev on 2011-05-01
jean@ubuntu:~$ rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
rm: impossible de supprimer «/home/jean/.pulse»: Aucun fichier ou dossier de ce type
rm: impossible de supprimer «/home/jean/.asound*»: Aucun fichier ou dossier de ce type

jean@ubuntu:~$ sudo rm /etc/asound.conf
[sudo] password for jean: 
rm: impossible de supprimer «/etc/asound.conf»: Aucun fichier ou dossier de ce type
jean@ubuntu:~$ 


I don't have any of those files and I don't know how to visualize them ...

---

### Post by jrev on 2011-05-01
Now everything works fine !
Thanks for your help :P

---

### Post by hakermania on 2011-05-01
Hey, if you want, please post here the way you followed in order to solve your problem and mark the thread as solved.

---

