---
title: "error running a command in the terminal"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by ninja senses on 2009-07-06
Hey guys I was trying to run this command:

```
sudo apt-get install automoc kdebase-workspace-dev libplasma-dev libboost-dev kdepimlibs5-dev libtag1-dev 
```

but I get the following error:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kdepimlibs5-dev: Depends: libboost1.35-dev but it is not going to be installed
E: Broken packages

```

can someone help me out?

---

### Post by glennric on 2009-07-06
Try running 
```
sudo apt-get update
```
first.  Then run your command again.  libboost1.35-dev is in the main repositories, and should be automatically installed if you try to install kdepimlibs5-dev.

---

### Post by glennric on 2009-07-06
Oh wait.  libboost1.35-dev conflicts with libboost-dev.  Take libboost-dev out of your command and libboost1.35-dev will be installed to satisfy the dependencies of kdepimlibs5-dev.

---

### Post by ninja senses on 2009-07-06
> **glennric said:**
> Try running 
```
sudo apt-get update
```
first.  Then run your command again.  libboost1.35-dev is in the main repositories, and should be automatically installed if you try to install kdepimlibs5-dev.

hmmm still no luck...

---

### Post by ninja senses on 2009-07-07
> **glennric said:**
> Oh wait.  libboost1.35-dev conflicts with libboost-dev.  Take libboost-dev out of your command and libboost1.35-dev will be installed to satisfy the dependencies of kdepimlibs5-dev.

oh  this seems to be working...thanks!!

---

