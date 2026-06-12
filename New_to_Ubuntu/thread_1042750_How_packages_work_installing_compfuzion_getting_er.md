---
title: "How packages work/ installing compfuzion getting error"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Bandanna on 2009-01-17
I've googled and downloaded a package for simple-ccsm when I ran it it said it was dependent on python which to my understanding is a scripting language.
There are many things to download regarding Python and it all is quite confusing really... especially with not being used to this interface and all.
I also see that you can install simple-ccsm through synaptics but it doesn't show the package when I search under "all".
I'm assuming that is why I receive this; E: Couldn't find package simple-ccsm
when using the terminal code that has been suggested in other threads.

Here is full terminal code:

zack@ubuntu:~$ sudo apt-get install simple-ccsm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package simple-ccsm
zack@ubuntu:~$ sudo apt-get install ccsm

I've also tried this one:

zack@ubuntu:~$ sudo apt-get install simple-ccsm compiz-config-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package simple-ccsm

I've installed Ubuntu 8.10 inside Windows if maybe that might have anything to do with my problem.

Thank you for the help! =]

---

### Post by nhasian on 2009-01-17
compiz is already installed by default with ubuntu.  you only need to install the ccsm if you want to tinker with the compiz config settings

```
sudo apt-get install compizconfig-settings-manager
```

you dont need simple-ccsm

---

### Post by 2hot6ft2 on 2009-01-17
try running ```
sudo apt-get update
``` first and I don't know if being installed inside windows would make a difference or not as I've always opted for real installs. It does work on a real install.

---

### Post by mrbiggbrain on 2009-01-17
sudo apt-get update

that will get new lists from all the repositorys in your list file

beat to it

---

### Post by Bandanna on 2009-01-17
Thank you!
Quick reply's that worked.

Ran update code (took a min or two)
then the install code, terminal did its thing and it worked.

Thank you problem solved.
And apparently it does not matter if installed through windows. =]
thank you very much guys

---

### Post by mrbiggbrain on 2009-01-17
theres also


```
sudo apt-get upgrade
```


that should update your ubuntu box :-)

---

