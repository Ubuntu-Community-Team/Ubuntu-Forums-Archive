---
title: "howto update linux kernel-packages with terminal without gui Update Manager?"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by user34532 on 2009-07-20
If sudo apt-get update && sudo apt-get upgrade command is run, all packages should be updated.

But when gui Update Manager is launched, *System > Administration > Update Manager*,
it shows that there is more packages to be updated, Linux-headers, Linux-images-*, etc. 

Those packages dont update just running  sudo apt-get upgrade.

Howto update also those kernel packages using command line? I don't want to use gui to update my system.

---

### Post by /usr/sbin on 2009-07-20
Open terminal and type the following commands:
$ sudo apt-get update

Now search kernel version:
$ apt-cache search kernel-image

Now install kernel by explicitly specifying version number:
$ sudo apt-get install linux-image-2.6.xx-yy-generic

Replace xx.yy with kernel version number. Reboot the system.

Thats how I did it. Hope it helps.

---

### Post by snek on 2009-07-20
First of all, why use apt-get?
My kernels always update automatically but I am using aptitude instead.

```

sudo aptitude update
sudo aptitude safe-upgrade
sudo aptitude full-upgrade

```

Should do the trick usually..

---

### Post by Mornedhel on 2009-07-20
> **user34532 said:**
> If sudo apt-get update && sudo apt-get upgrade command is run, all packages should be updated.

No, all packages that can be updated without installing or removing other packages will be updated. The rest will be held back. To install those, you can use aptitude as another poster suggested, or run sudo apt-get dist-upgrade instead of sudo apt-get upgrade.

---

### Post by abalo13 on 2013-04-14
I just installed  ubuntu server, how can I install the latest version of the linux kernel? I dont have a GUI, how can I even download it if i dont have  browser, my pc is full connected to the internet, I just have the x windows to use commands. please help. I want the the version [B]3.8.7        
thanks everyone for your help.[/B]

---

### Post by sandyd on 2013-04-14
**Necromancing - Thread closed**
Please do not post in threads more than one year old as many things change between Ubuntu releases and the solutions provided in the thread may not be pertinent to your installation.

Thanks!

---

