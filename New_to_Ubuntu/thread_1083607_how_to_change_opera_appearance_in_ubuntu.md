---
title: "how to change opera appearance in ubuntu"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by gkraju on 2009-03-01
hi i am using ubuntu 8.04 
i am using opera but the appearance looks wierd(it is like windows 98)
is there any way i change it 
thanks in advance

---

### Post by gandaran on 2009-03-01
opera is a KDE browser, uses qt libs so it doesn't look very nice running in gnome.
download and install the static qt4 version, this one integrates better in gnome.

---

### Post by gkraju on 2009-03-01
> **gandaran said:**
> opera is a KDE browser, uses qt libs so it doesn't look very nice running in gnome.
download and install the static qt4 version, this one intregrates better in gnome.
thanks for your reply 
but i am new to ubuntu 
can you tell the command exactly

---

### Post by gjoellee on 2009-03-01
here you go:
```
sudo apt-get install qt4
```I don't use Ubuntu, so I don't know if the package exists, but you could do a try :P
(maybe you don't need "4" after "qt").

---

### Post by gkraju on 2009-03-01
> **gjoellee said:**
> here you go:
```
sudo apt-get install qt4
```I don't use Ubuntu, so I don't know if the package exists, but you could do a try :P
(maybe you don't need "4" after "qt").

when i type this command it says couldnt find package qt4 
and couldnt find package qt(if i left 4  from qt)

---

### Post by gandaran on 2009-03-01
download the opera qt4 .deb package[ here]("ftp://ftp.opera.com/pub/opera/linux/963/final/en/i386/") remove the other opera first.

---

