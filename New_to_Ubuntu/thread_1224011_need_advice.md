---
title: "need advice"
date: 2009-07-26
forum: New to Ubuntu
---

### Post by stalkier on 2009-07-26
I have a AMD custom built system. it has:

AMD Athlon X2 4000+ 2.1GHrz
2.5GB DDR running 400MHrz
XFX GeForce 8 8500GT (running 512MB GDR),
DVD writer (IDE)

OS: stricly Ubuntu Linux 9.04 (for now)

I would like to know what the best thing for me to do. I have the OS right now running off of a external hdd. I am changing it to a SATA 320GB on Tuesday. How and what do I need to get a lists of apps I have installed. Is there a way to generate the lists and then put them in a bash command of some sort. To run an automated apt-get or whatever. to restore the apps.

---

### Post by ~sHyLoCk~ on 2009-07-26
First put them in a file:
```
dpkg –get-selections | grep -v deinstall > apps
```
When you reinstall ubuntu:
   ```
 sudo apt-get update

    sudo apt-get dist-upgrade

    dpkg –set-selections < apps
    
    sudo dselect
```

---

### Post by stalkier on 2009-07-26
> **~sHyLoCk~ said:**
> First put them in a file:
```
dpkg –get-selections | grep -v deinstall > apps
```
When you reinstall ubuntu:
   ```
 sudo apt-get update

    sudo apt-get dist-upgrade

    dpkg –set-selections < apps
    
    sudo dselect
```

Ok so I can do these commands and it will save the file to my desktop or whereever. I can the just navigate to the file and use the other sudos. Then will they be all installed like before?

---

### Post by llamabr on 2009-07-26
To get better advice, have a more informative subject line.

You'll find all of your .deb's in /var/cache apt/archives/

---

### Post by ~sHyLoCk~ on 2009-07-26
> **llamabr said:**
> To get better advice, have a more informative subject line.

You'll find all of your .deb's in /var/cache apt/archives/

This is prolly simpler, just copy the cache packages to the new install and run ```
dpkg -i *.deb
```

---

### Post by DGortze380 on 2009-07-27
Look into remastersys. May serve you better than a list of apps

---

### Post by stalkier on 2009-09-02
Thanks guys. Really appreciate all the help.

---

