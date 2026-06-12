---
title: "WPA2 using Howto- 'make' command not working :("
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by kendals on 2006-08-29
Hi guys.

I just followed the guide at [http://www.ubuntuforums.org/showpost.php?p=130227p=423584](http://www.ubuntuforums.org/showpost.php?p=130227p=423584) and got to this part:

```
cd ..
cd ieee80211-1.0.3
make
sudo make install
```

But it tells me I can't use 'make' command, so it's not working. Please help me, as I've removed the old drivers first, so I don't have ANY wireless now (at least had unsecured working before).

What am I doing wrong? I am typing 'make' at the correct directory, in terminal, as root user, using 6.06 LTS, with Intel 2915ABG chipset.

Thanks!

---

### Post by AndyCR on 2006-08-29
By default make is not included with Ubuntu. To fix this, type this in the terminal:

sudo apt-get install gcc g++ make

---

### Post by kendals on 2006-08-29
Thanks for the quick reply, Andy :)

This is what it is saying...

```
sudo apt-get install gcc g++ make
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils cpp cpp-4.0 g++-4.0 gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers
Suggested packages:
  binutils-doc cpp-doc gcc-4.0-locales gcc-4.0-doc lib64stdc++6 manpages-dev
  autoconf automake1.9 libtool flex bison gcc-doc libc6-dev-amd64 lib64gcc1
  glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils cpp cpp-4.0 g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 1407kB/11.8MB of archives.
After unpacking 46.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://security.ubuntu.com dapper-security/main binutils 2.16.1cvs20060117-1ubuntu2.1
  Temporary failure resolving 'security.ubuntu.com'
Media change: please insert the disc labeled
 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
in the drive '/cdrom/' and press enter

Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/g/gcc-4.0/cpp-4.0_4.0.3-1ubuntu5_i386.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

So I tried inserting the cd that Ubuntu sent me (version used to install it), and it still stuffed up, since it can't connect to grab the file, and it couldn't retrive another file from the cd. I don't know how else to get it to use the 'make' command :(

---

### Post by kendals on 2006-08-29
*bump*

I know you're probably all busy, but I'm desparate. Pretty please! :(

---

### Post by AndyCR on 2006-08-29
That's odd. Try:

sudo apt-get update
sudo apt-get install gcc g++ make

---

### Post by kendals on 2006-08-29
> **AndyCR said:**
> That's odd. Try:

sudo apt-get update
sudo apt-get install gcc g++ make

Unfortunately, that requires being connected to the net, which is only happening in XP right now, so I'm constantly restarting, and I tried this, but it said it couldn't connect, for obvious reasons, to the Ubuntu servers...:confused:

---

### Post by kendals on 2006-08-30
Solved the problem. Found a solution at [http://ubuntuforums.org/showpost.php?p=1081852&postcount=6](http://ubuntuforums.org/showpost.php?p=1081852&postcount=6) :)

---

