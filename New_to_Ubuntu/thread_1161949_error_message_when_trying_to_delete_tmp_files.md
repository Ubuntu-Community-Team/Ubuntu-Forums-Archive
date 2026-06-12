---
title: "error message when trying to delete tmp files"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-05-17
this worked great until this am note the error message i get how can i fix as always tks


ray@ray-desktop:~$ sudo rm -rf /tmp/*
sudo: unable to resolve host ray-desktop
ray@ray-desktop:~$

---

### Post by rburkartjo on 2009-05-17
also note following errors

ray@ray-desktop:~$ sudo -i
sudo: unable to resolve host ray-desktop
root@ray-desktop:~# sudo su
sudo: unable to resolve host ray-desktop

---

### Post by Didius Falco on 2009-05-17
Hi,

I found this through Google:

[http://www.nabble.com/unable-to-resolve-host-...-td20495139.html](http://www.nabble.com/unable-to-resolve-host-...-td20495139.html)

I hope it helps...

Regards,

Didius

---

### Post by rburkartjo on 2009-05-17
tks did but still lost

---

### Post by Didius Falco on 2009-05-17
Here are a couple more leads for you:

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

[http://www.kubuntuforums.net/forums/index.php?topic=3092772](http://www.kubuntuforums.net/forums/index.php?topic=3092772)


[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906)

Regards,

Didius

---

### Post by rburkartjo on 2009-05-17
did tks the first link on your last reply did the trick

---

