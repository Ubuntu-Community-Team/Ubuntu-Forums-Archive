---
title: "dpkg error"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by ironmaiden943 on 2009-02-06
I try to install a program through the terminal and it tells me: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

so i run dpkg --configure -a as it tells me to do and i get the following:

andrea@andrea-laptop:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu16) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

Splashy ERROR: Cannot read XML File <</etc/splashy/config.xml>>. Exiting...
Splashy ERROR: Error occured while starting Splashy
Make sure that you can read Splashy's configuration file

cp: cannot stat `/etc/splashy/config.xml': No such file or directory

Please help, i have no idea what to do!

---

### Post by sandyd on 2009-02-06
you have to install libsplashy before installing splashy :)

---

### Post by ironmaiden943 on 2009-02-06
> **carlee said:**
> you have to install libsplashy before installing splashy :)
how do i install libsplashy? i cannot open synaptic or run apt-get without getting E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by taurus on 2009-02-07
I guess you just have to download it and install it by hand first then (if you are using intrepid).

[http://packages.ubuntu.com/intrepid/libsplashy1](http://packages.ubuntu.com/intrepid/libsplashy1)

---

### Post by DGortze380 on 2009-02-07
> **ironmaiden943 said:**
> how do i install libsplashy? i cannot open synaptic or run apt-get without getting E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

sudo apt-get remove splashy
sudo dpkg --configure -a
sudo apt-get install libsplashy && sudo apt-get install splashy

---

### Post by ironmaiden943 on 2009-02-07
i tried to install and it tells me that a later version is already installed so i'm guessing that not having libsplahy installed is not the problem?

---

### Post by DGortze380 on 2009-02-07
can you post the output of
```
cat /etc/splashy/config.xml
```

You'll probably want to add 

```
 | less
```

to the end of that first command fi the file is too long to fit in the terminal.

---

### Post by ironmaiden943 on 2009-02-07
cat: /etc/splashy/config.xml: No such file or directory

---

### Post by mc4man on 2009-02-07
> so i'm guessing that not having libsplahy installed is not the problem?
If anything that is what's installed.

> i tried to install and it tells me that a later version is already installed

You may want to be a little more verbose and post the complete terminal output from any of the apt-get remove or install commands in post 5. In the above case a later version of what?


If you tried the suggestion in post 4 what was the outcome and or message from Gdebi?

you might want to post your sources list.

```
cat /etc/apt/sources.list
```

---

### Post by sandyd on 2009-02-08
> **ironmaiden943 said:**
> i tried to install and it tells me that a later version is already installed so i'm guessing that not having libsplahy installed is not the problem?

try

```

sudo apt-get remove splashy
sudo apt-get -f install
sudo apt-get install splashy

```THEN open synapatic and install splashy

seems that the versions of splashy are different, so their probably not compatible.

EDIT: seems like several people have the same problemma as you
[http://ubuntuforums.org/archive/index.php/t-822328.html](http://ubuntuforums.org/archive/index.php/t-822328.html)

Also might want to try here(post4)


[http://ubuntuforums.org/showthread.php?t=37518#](http://ubuntuforums.org/showthread.php?t=37518#)

---

