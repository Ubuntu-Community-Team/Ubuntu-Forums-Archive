---
title: "dpkg was interrupted"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Ghost M.D on 2009-02-22
Hi all

I was installing kde 3.5

from this 

[http://apt.pearsoncomputing.net/]("http://apt.pearsoncomputing.net/")

after that I reboot my computer

the kde does not work

when I longed on be gnome I see crash report about some bakages

I use these lines but I did not work

sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get --fix-missing install

```
ahmad@ahmad-laptop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0166' near line 1:
 newline in field name `#padding'
ahmad@ahmad-laptop:~$ sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
ahmad@ahmad-laptop:~$ sudo apt-get --fix-missing install
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

I can not install anything also

what I can do..?

---

### Post by yeats on 2009-02-22
Okay....

So to be clear, you're running regular Ubuntu and want to add KDE?  Are you running Intrepid, which is why you're trying to install KDE 3.5 from source?

Installing a huge program like KDE from source is probably not a good idea until you have a better handle on what's what.  

As far as the apt-get error goes, it looks like there's a typo in one of the scripts being accessed - either that or there's a missing dependency somewhere that keeps the script from being read correctly. (That's my take, anyway).

---

### Post by spiderbatdad on 2009-02-22
check for a file called /var/lib/dpkg/lock you can safely remove that file.

---

### Post by Ghost M.D on 2009-02-22
> **chrissharp123 said:**
> Okay....

So to be clear, you're running regular Ubuntu and want to add KDE?  Are you running Intrepid, which is why you're trying to install KDE 3.5 from source?

Installing a huge program like KDE from source is probably not a good idea until you have a better handle on what's what.  

As far as the apt-get error goes, it looks like there's a typo in one of the scripts being accessed - either that or there's a missing dependency somewhere that keeps the script from being read correctly. (That's my take, anyway).

yes I want to install KDE on regular Ubuntu , also yes I running 8.10 , I installed 4.1 before it & I like it but it was unstable so I was need to remove it & after I remove it the kernel damaged ((kernel panic)) after that I reinstall the kernel & I want to install stable version of KDE 
so I install 3.5

---

### Post by howefield on 2009-02-22
kubuntu-desktop is the package in the Ubuntu repository which will give you KDE 3.5.

Can you reverse what you have done, and install that ?

At least you'll be using a trusted repository.

---

### Post by Ghost M.D on 2009-02-22
> **spiderbatdad said:**
> check for a file called /var/lib/dpkg/lock you can safely remove that file.

how ..?

I go to dpkg file but I cannot delete it

---

### Post by Ghost M.D on 2009-02-22
> **howefield said:**
> kubuntu-desktop is the package in the Ubuntu repository which will give you KDE 3.5.

Can you reverse what you have done, and install that ?

At least you'll be using a trusted repository.

sorry I did not understand

can you get it more clear

---

### Post by yeats on 2009-02-22
> kubuntu-desktop is the package in the Ubuntu repository which will give you KDE 3.5.

Can you reverse what you have done, and install that ?

At least you'll be using a trusted repository. 

This is true in Hardy Heron, but KDE 3.5 on Intrepid is more complex and involved (and not recommended as far as I've read).  I also prefer KDE 3.5, so I actually rolled back (reinstalled) to Hardy on two of my Linux installations.  I'm sure if you Google "KDE 3.5 Intrepid" you'll get advice (and a lot of grousing about KDE 4.1) :-).

In any case, Ghost M. D. - I suggest aborting your mission, at least until you know more about how installation really works.  You can back up your data and have Hardy up and running in less time than it will take to sort this out. :-)

---

### Post by spiderbatdad on 2009-02-22
find the lock file```
ls /var/lib/dpkg/
```
remove it:
```
sudo -i
rm /var/lib/dpkg/lock
apt-get install -f
```

---

### Post by Ghost M.D on 2009-02-22
```
ahmad@ahmad-laptop:~$ cd /var/lib/dpkg/
ahmad@ahmad-laptop:/var/lib/dpkg$ ls /var/lib/dpkg/
alternatives   cmethopt        info   statoverride      status-old
available      diversions      lock   statoverride-old  triggers
available-old  diversions-old  parts  status            updates
ahmad@ahmad-laptop:/var/lib/dpkg$ sudo -i
[sudo] password for ahmad: 
root@ahmad-laptop:~# rm /var/lib/dpkg/lock
root@ahmad-laptop:~# apt-get install -f
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

for bad it did not work

---

### Post by spiderbatdad on 2009-02-22
make sure you dont have any package managers running...that synaptic is closed. remove lock again... try running apt-get autoremove, run dpkg --configure -a
You can only run package managers one at a time; that is you can't run apt from the terminal while synaptic is open.

---

### Post by Ghost M.D on 2009-02-22
I fix it

I delete the file 0166 by rm

& it works agien

thank you

---

