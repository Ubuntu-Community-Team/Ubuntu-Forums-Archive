---
title: "Can't start openbox"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by theozzlives on 2009-03-26
Well I installed openbox on my test computer through synaptic and when I tried to boot the session I got an error saying my session lasted 10 seconds and I was out of disk space. My test computer has 15 GB free.

So I installed it on my laptop that has 90 GB free, same thing. What am I doing wrong?

---

### Post by taavikko on 2009-03-26
Is this happening release version below 9.04? or in Jaunty?

You obviously tried selecting from gdm menu that session is openbox?

---

### Post by theozzlives on 2009-03-27
It's happening in Intrepid and yes, that's the only way I could see to run it (GNOME + OpenBox)

---

### Post by KIAaze on 2009-03-27
Do you have multiple partitions?
I think what's most important is to have enough free space in /tmp and maybe /var.

I use openbox and I never encountered this problem. O.o
I did however encounter it with Gnome a few times. Usually "sudo apt-get clean" was enough to solve it.

---

