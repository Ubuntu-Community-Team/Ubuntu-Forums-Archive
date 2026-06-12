---
title: "Deluge update"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by ovisan on 2009-05-13
lo lads

Quick question: how do I update Deluge to 1.1.7?


I ve downloaded deluge_1.1.7.orig.tar.gz and tried to follow the instructions:

```
sudo apt-get install g++ make python-all-dev python-all python-dbus
```  done, but 
```
 python-gtk2 python-notify librsvg2-common python-xdg python-support
```  shows me a 
```
bash: python-gtk2: command not found
``` same wit thm: 
```
subversion libboost-dev libboost-python-dev libboost-iostreams-dev \
    libboost-thread-dev libboost-date-time-dev libboost-filesystem-dev \
    libboost-serialization-dev libssl-dev zlib1g-dev python-setuptools
```and 
```
$ python setup.py build
```gives me: 
```
python: can't open file 'setup.py': [Errno 2] No such file or directory
```
I m a mega noob. Please tell me what I m doing wrong!!!

Cheers

---

### Post by Ragnar Bocephus on 2009-05-13
Which version do you have installed currently?

Personally, I would forget about building it from source and add this ppa to your /etc/apt/sources.list, following these instructions:

[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

After that's done and the security key is successfully added, you can 

```
sudo apt-get update && sudo apt-get upgrade
```

and it should automatically prompt you to install 1.1.7 and any other future releases.

---

### Post by ovisan on 2009-05-13
> **Ragnar Bocephus said:**
> Which version do you have installed currently?

Personally, I would forget about building it from source and add this ppa to your /etc/apt/sources.list, following these instructions:

[https://launchpad.net/~deluge-team/+archive/ppa]("https://launchpad.net/%7Edeluge-team/+archive/ppa")

After that's done and the security key is successfully added, you can 

```
sudo apt-get update && sudo apt-get upgrade
```and it should automatically prompt you to install 1.1.7 and any other future releases.



Cheers mate!  Sorted!

---

