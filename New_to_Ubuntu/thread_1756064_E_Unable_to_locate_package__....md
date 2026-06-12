---
title: "E: Unable to locate package  ..."
date: 2011-05-11
forum: New to Ubuntu
---

### Post by Loufa on 2011-05-11
Hello,

i am new to ubunto. i am  trying to install some tools when i add the following command :

sudo apt-get -y install libsigc++-2.0-dev subversion binutils-dev mpi-default-dev g++ g++-4.4 gccxml libgfortran3 libibverbs-dev libibverbs1 libicu-dev libicu42 libnuma1 libopenmpi-dev libopenmpi1.3 libstdc++6-4.4-dev openmpi-common python-dev python2.6-dev ia32-libs patch automake libboost1.42-dev libboost1.42-all-dev libboost-dbg libboost-thread1.42.0 libboost-system1.42.0 libboost-regex1.42.0 libboost-program-options1.42.0 libboost-filesystem1.42.0

]i receive the following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libicu42

when i try different solutions i got the same error but with different package.

can any one help me ??

thanks

---

### Post by Wobblybob on 2011-05-13
you are probably trying to install packages that are not available libicu42 is now libicu44 on Ubuntu 11.04 try opening the synaptic package manager and checking the available packages and or installing then from there

---

### Post by wojox on 2011-05-13
```
sudo apt-get update; sudo apt-get install build-essential
```

---

### Post by Loufa on 2011-05-13
Thanks
my problem solved by checking and installing packages .

---

