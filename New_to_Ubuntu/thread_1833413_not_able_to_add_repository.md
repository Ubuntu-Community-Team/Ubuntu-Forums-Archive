---
title: "not able to add repository"
date: 2011-08-26
forum: New to Ubuntu
---

### Post by amitpokhrel on 2011-08-26
HI my net is running under proxy server. I configured it to work under proxy. everything is working fine (apt-get update) but when i try to add repositories nothing happens....
is there another way i can add repository??

---

### Post by LowSky on 2011-08-26
what repos are you trying to add?

what version of Ubuntu are you using?

Are you sure you can access the repo? in other words can you ping it or use a browser to visit the site?

---

### Post by amitpokhrel on 2011-08-26
i am using 10.10
I was trying to install ubuntu tweek...

---

### Post by flurospar on 2011-08-26
Is the repo added correctly?

First, remove the added repo from System > Administration > Software Sources.

Then, reload the repository information if the package manager wants to.

Then, in a terminal, type:
```

sudo add-apt-repository ppa:somerepository/ppa

```
replacing somerepository/ppa with the location of the repository of Ubuntu tweak.
Finally, type this:```
sudo apt-get update
```

Check if Ubuntu tweak appears in Synaptic. If it doesn't, download the Ubuntu tweak deb by yourself and install it by double clicking on it. This should hopefully make all the packages of the Ubuntu tweak repo available.

(Note that this might not work for you. I followed the above when I couldn't install chromium from chromium-daily/ppa)

---

### Post by amitpokhrel on 2011-09-07
I got the solution!!!
when I type command to add repository and hit enter, the terminal shows busy and doesn't tell if the repository is added or not. but when i cancel it(cntrl+z) and check the synaptic, the repository is added. I thing this is a bug in ubuntu11.04

---

### Post by pappusarkar on 2011-09-07
Use Y PPA Manager.It is a GUI Based ppa management tool.

in Terminal

sudo add-apt-repository ppa:webupd8team/y-ppa-manager sudo apt-get update sudo apt-get install y-ppa-manager

---

