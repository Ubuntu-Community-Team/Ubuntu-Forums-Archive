---
title: "About Update Manager"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by aroha on 2009-07-04
Good day !

):P

Got a question fot you :

When I get my update manager opened, it says "liblucene2-java" on the box, but it is **Not** highlighted so I can not check the box and install/update this engine library...What should I do to fix it ?
Thank you friends for all your support !
[http://ubuntuforums.org/showthread.php?p=7561100#post7561100](http://ubuntuforums.org/showthread.php?p=7561100#post7561100) 
Aroha
PS- I am running ubuntu netbook remix (9.04) on a netbook acer aspire one

---

### Post by cariboo on 2009-07-06
Try a different server, as the one you are using may not have all the right dependencies.

---

### Post by sadaruwan12 on 2009-07-06
Hi,

Open the terminal and type,

```
sudo apt-get autoclean
```

after that finishers type,

```
sudo apt-get autoremove
```

and go to system -> administration -> Synaptic Package manager after opening that up click on status button and check the above text panel where you might see something like this "Not Installed (residual config)" click that and remove all the residual programs there 'cos those are left overs from previously removed programs.

In the update manger some times these programs get listed but cannot be updated due to those programs are not installed in the system any more but they are there as residue so clean this will solve your problem.

---

