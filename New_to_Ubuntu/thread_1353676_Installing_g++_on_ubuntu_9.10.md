---
title: "Installing g++ on ubuntu 9.10"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by brett01 on 2009-12-13
Hi,

       I am an absolute beginner to ubuntu.I installed ubuntu 9.1 succesfully. I want to install g++ to do my c++ programming.

By googling I got the command sudo apt-get install build-essential but Im unable to compile my c++ programs. Can someone help me pls.

> ~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  language-pack-bn: Depends: language-pack-bn-base (>= 1:9.10+20091022) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



Thanks & Regards,
brett.

---

### Post by Physical Hook on 2009-12-13
What if you follow the advice ?

```
sudo apt-get -f install
```

---

### Post by Temposs on 2009-12-13
Alternatively, try this:

```
sudo apt-get install language-pack-bn
```

and then do the original command again:

```
sudp apt-get install build-essential
```

---

### Post by brett01 on 2009-12-13
> **Temposs said:**
> Alternatively, try this:

```
sudo apt-get install language-pack-bn
```and then do the original command again:

```
sudp apt-get install build-essential
```


Thank you very much .This is working for me.

---

### Post by nanometer on 2010-07-18
It doesn't work for me i get this error again:

milad@milad-laptop:~/Desktop/Zigorat/src$ sudo apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages

tnx

---

### Post by theozzlives on 2010-07-18
> **nanometer said:**
> It doesn't work for me i get this error again:

milad@milad-laptop:~/Desktop/Zigorat/src$ sudo apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: g++ (>= 4:4.3.1) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
E: Broken packages

tnx

Are you running a Beta Version of Ubuntu?

---

