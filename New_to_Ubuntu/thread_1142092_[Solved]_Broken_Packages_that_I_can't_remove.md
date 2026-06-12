---
title: "[Solved] Broken Packages that I can't remove"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2009-04-28
Hi,

I tried to install a software package earlier today and it failt.
How can I fix my system please?


Here is the output:
```

User@UbuntuBox:~$ sudo apt-get clean all
User@UbuntuBox:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libc6 libc6-i686
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc6 libc6-i686
2 upgraded, 0 newly installed, 0 to remove and 1083 not upgraded.
3 not fully installed or removed.
Need to get 5785kB of archives.
After this operation, 250kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  libc6 libc6-i686
Install these packages without verification [y/N]? y
Get:1 http://ftp.de.debian.org sid/main libc6 2.9-8 [4551kB]
Get:2 http://ftp.de.debian.org sid/main libc6-i686 2.9-8 [1233kB]              
Fetched 5785kB in 13s (427kB/s)                                                
Preconfiguring packages ...
(Reading database ... 185408 files and directories currently installed.)
Preparing to replace libc6 2.8~20080505-0ubuntu9 (using .../archives/libc6_2.9-8_i386.deb) ...
Checking for services that may need to be restarted...
Checking init scripts...
Unpacking replacement libc6 ...
dpkg: error processing /var/cache/apt/archives/libc6_2.9-8_i386.deb (--unpack):
 trying to overwrite `/usr/share/man/man1/localedef.1.gz', which is also in package belocs-locales-bin
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.9-8_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ptn107 on 2009-04-28
First things first.  You need to get rid of the Debian repositories from your software sources.  Mixing Ubuntu and Debian sources will break your system, period.  Press ALT+F2 and type **gksu gedit /etc/apt/sources.list**, remove any lines referencing *[http://ftp.de.debian.org](http://ftp.de.debian.org) sid/main*.  Save the file and run the following commands in order to try and sort things out:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade -y
```

---

### Post by Mega_Fauna on 2009-04-28
> **ptn107 said:**
> First things first.  You need to get rid of the Debian repositories from your software sources.  Mixing Ubuntu and Debian sources will break your system, period.  Press ALT+F2 and type **gksu gedit /etc/apt/sources.list**, remove any lines referencing *[http://ftp.de.debian.org](http://ftp.de.debian.org) sid/main*.  Save the file and run the following commands in order to try and sort things out:
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get dist-upgrade -y
```

Hi,

Thanks for your rapid response. I have done all the steps you listed and here is the result:

```
User@UbuntuBox:~$ sudo apt-get dist-upgrade -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.9-8) but 2.8~20080505-0ubuntu9 is installed
E: Unmet dependencies. Try using -f.
```


Then I ran (as suggested):

```
apt-get -f install
```

Fixed two broken keys (a separate problem) and my system runs! Thanks alot:D

---

