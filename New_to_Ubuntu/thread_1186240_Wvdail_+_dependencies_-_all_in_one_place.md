---
title: "Wvdail + dependencies - all in one place?"
date: 2009-06-13
forum: New to Ubuntu
---

### Post by chome4 on 2009-06-13
Simply saying wvdial is needed in Jaunty isn't as simple as that. It needs other files to be installed and in some cases those files need other files and so on....
 
Are there any locations where I can download the everything I need to get wvdial going in jaunty?

---

### Post by Mornedhel on 2009-06-13
Um.

There is a wvdial package in the repositories. You can install it through Synaptic or with

```
sudo apt-get install wvdial
```

In case you really want to build it from source you can try sudo apt-get build-dep wvdial if you have source repositories enabled.

---

### Post by chome4 on 2009-06-13
> **Mornedhel said:**
> Um.
 
There is a wvdial package in the repositories. You can install it through Synaptic or with
 
```
sudo apt-get install wvdial
```
 
In case you really want to build it from source you can try sudo apt-get build-dep wvdial if you have source repositories enabled.
 
I'll give that a go. 
 
Thank you.

---

### Post by chome4 on 2009-06-13
Error message I got when I ran the command:
 
sudo apt-get install wvdial
error
p@p:~$ sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Package wvdial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wvdial has no installation candidate
p@p:~$

---

### Post by Mornedhel on 2009-06-13
Weird. According to the package, it should be in Jaunty's main repositories. Have you updated your package list ?

I have tried to install it here and it works (well, the install works).

---

### Post by chome4 on 2009-06-14
[https://answers.launchpad.net/ubuntu/+question/73099](https://answers.launchpad.net/ubuntu/+question/73099)

GeorgeVita's reply works if you follow it to the letter. All you have to do is edit the wvdial.conf file.

---

