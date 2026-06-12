---
title: "installing Giza++ under ubuntu 10.10"
date: 2011-03-16
forum: New to Ubuntu
---

### Post by wafadz on 2011-03-16
Hi, i'll be grateful to you if you help me, i tried to install Giza++ under ubuntu 10.10
Giza++ was installed but when i tried to run the Makefile i had compilation errors
and i coudln't install gcc , do you have any idea regarding this issue?
 
thanks

---

### Post by rosencrantz on 2011-03-16
gcc is in build-essentials (via apt-get or synaptic). This should include the make utility, so I'm a bit puzzled you got compilation errors instead of 'make not found'. 
Anyway, I got the giza-pp sources, untarred and ran make, which worked. Alternatively, you could try debs from this repository, [http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/lucid/nlp/](http://cl.naist.jp/~eric-n/ubuntu-nlp/dists/lucid/nlp/), but the most recent distribution they support is lucid.

Cheers, 
rosencrantz

---

