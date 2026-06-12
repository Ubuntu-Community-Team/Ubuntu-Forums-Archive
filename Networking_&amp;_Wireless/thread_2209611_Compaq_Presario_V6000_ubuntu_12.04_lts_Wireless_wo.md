---
title: "Compaq Presario V6000 ubuntu 12.04 lts Wireless wont work"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by David_Wilson on 2014-03-06
Hi All,

Im completely new to ubuntu and all of my previous computer experience is with windows so I would really appreciate all the help i can get.
I have looked through forum after forum and I still cant make sense of it.
I freshly installed ubuntu 12.04 lts from CD last night and although I can get an internet connection through an ethernet cable, I dont pick up any wireless connections.
Please help :)

---

### Post by Hadaka on 2014-03-06
HI ,while connected with the ethernet to the internet please open a terminal...ctrl/alt/t and  do..
```
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```, your wireless should
now be working,
 *IF NOT
then please post the output of..
```
lspci | grep -iA3 net
```
thanks.

---

### Post by David_Wilson on 2014-03-06
Hi thats worked, thanks

---

### Post by mörgæs on 2014-03-06
Good, then please mark the thread 'solved'.

---

