---
title: "Problem with graphic card"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by Trivi on 2009-05-06
I've got a dell m1530 and have intrepid, i have loads of problems with the graphics, i need to instal the Nvidia 185.19 but this instalation i found is for hardy (link below)

[http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185](http://ubuntuforums.org/showthread.php?t=1125400&highlight=nvidia+185)

What may I do??

i just follow that installation process? or is there another process i have to follow?

---

### Post by Didius Falco on 2009-05-06
I just had a quick read-through of the HowTo and the part dealing with that driver states:

> For the **185.19** drivers (Recommended OS's are: Hardy, Intrepid or Jaunty or a 2.6.28 or earlier kernel):Just follow the HowTo carefully, and you should be fine.  Tinivole is what I consider a Trusted Source for information.

I hope this helps, and welcome to the community!

Regards,

Didius

---

### Post by Trivi on 2009-05-06
The first step goes fine.... 

but second step (this code)
sudo apt-get install build-essential linux-headers-`uname -r`
doesn't go all right. It says that this step is to ensure that i have all the build-essencial problems and the answer my terminal give me is what follows:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.24-24-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-headers-2.6.24-24-generic has no installation candidate


Is that ok?

---

### Post by Didius Falco on 2009-05-06
I'd recommend posting in that HowTo thread. Tinivole seems to be keeping up with it, and I'd take advice on this from him over myself. Meanwhile, maybe someone else will post an answer in here that will be of more help than I can with this.

Regards,

Didius

---

