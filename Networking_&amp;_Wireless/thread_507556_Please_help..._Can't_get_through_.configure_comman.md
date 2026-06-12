---
title: "Please help... Can't get through ./configure command in modem installation"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by bar8080 on 2007-07-23
When I run ./configure it stops in C compiler.. here's the log please help...
[http://rapidshare.com/files/44517165/config.log.html](http://rapidshare.com/files/44517165/config.log.html)
Thanks...

---

### Post by renzokuken on 2007-07-23
run ```
sudo apt-get install build-essential
``` and try again

(you need internet connection for this, do you have one other than your modem?)

---

### Post by bar8080 on 2007-07-23
Thank you, but no I have 1 ALE 150 modem and connect from windows is there another way?

---

### Post by logos34 on 2007-07-23
if you're using 7.04 Feisty, you can get the deb pkg here:
**[http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/](http://archive.ubuntu.com/ubuntu/pool/main/b/build-essential/)**

Dowload it in windows, then copy it over to linux and install.

---

### Post by renzokuken on 2007-07-23
unfortunately build-essential is only a meta-package, which means it contains a list of things to downlaod and install, the actual components of build essential are

gcc
g++
make
dpkg-dev

you may have to get these one at a time on your windows install, transfer them to your linux install, and install them manually with 

```
sudo dpkg -i package_name.deb
```

but i dont know if the packages above have other dependencies. this sounds like a "dependancy hell" situation to me.

EDIT: just had a thought, the build-essential package and everything needed may well be on the install cd, have a look there first

DOUBLE EDIT: or have a look here [http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential) which lists what build-essential installs and links to each one individually

---

### Post by renzokuken on 2007-07-23
after reading around, it turns out the ECIADSL package has support for your modem.

have a look here for ECIADSL [http://eciadsl.flashtux.org/modems.php?modem=59](http://eciadsl.flashtux.org/modems.php?modem=59) and [http://eciadsl.flashtux.org/download.php](http://eciadsl.flashtux.org/download.php)

and here [http://ubuntuforums.org/showthread.php?t=140010&highlight=eciadsl](http://ubuntuforums.org/showthread.php?t=140010&highlight=eciadsl) for a how to on installing it

---

### Post by bar8080 on 2007-07-23
Thanks guys i made through the instalation i still have the synch problems i can't find the command to install a xx.tar.tar file other than that you helped a lot. THANK YOU:)

---

### Post by renzokuken on 2007-07-31
a tar file is simply an archive like a .zip or .rar file 

they commonly end with .tar.gz .tar.bz2 and a couple of other variations

you need to extract the contents first. usually a right click on the tar file and "extract here" does the trick

---

### Post by kevdog on 2007-07-31
Most are .tar.gz archives.

Here is the command to extract the files:

tar -zxvf ****.tar.gz

It will make a directory that you need to enter: cd *****

---

