---
title: "What happened to the build-essential in 9.10"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by dm6257 on 2009-11-08
I attempted to sudo apt-get install build-essential, I received the message 

Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate


Is there a replacement?

---

### Post by Menthu_Rae on 2009-11-08
It still exists mate. I think you should reload your software sources.

Go System > Administration > Software Sources

Choose an alternate location for "Download from:". Click close and reload when asked.

Then try to install it again...

```
**vmuser@virtual:~$ sudo apt-get install build-essential**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
Suggested packages:
  debian-keyring debian-maintainers g++-multilib g++-4.4-multilib gcc-4.4-doc
  libstdc++6-4.4-dbg libstdc++6-4.4-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-4.4 libstdc++6-4.4-dev patch
0 upgraded, 7 newly installed, 0 to remove and 38 not upgraded.
Need to get 6,999kB of archives.
After this operation, 23.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ftp.iinet.net.au karmic/main libstdc++6-4.4-dev 4.4.1-4ubuntu8 [1,490kB]
Get:2 http://ftp.iinet.net.au karmic/main g++-4.4 4.4.1-4ubuntu8 [4,701kB]
Get:3 http://ftp.iinet.net.au karmic/main g++ 4:4.4.1-1ubuntu2 [1,446B]        
Get:4 http://ftp.iinet.net.au karmic/main patch 2.5.9-5 [100kB]                
Get:5 http://ftp.iinet.net.au karmic/main dpkg-dev 1.15.4ubuntu2 [573kB]       
Get:6 http://ftp.iinet.net.au karmic/main build-essential 11.4 [7,172B]        
Get:7 http://ftp.iinet.net.au karmic/main fakeroot 1.12.4ubuntu1 [126kB]       
Fetched 6,999kB in 14s (483kB/s)                                               
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 117257 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.1-4ubuntu8_i386.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu8_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.1-1ubuntu2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu8) ...
Setting up g++-4.4 (4.4.1-4ubuntu8) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4) ...
vmuser@virtual:~$ 

```

---

### Post by Somme on 2009-11-08
Update your database:
```
sudo apt-get update
```

Install [build-essential]("http://packages.ubuntu.com/karmic/build-essential"):
```
sudo apt-get install build-essential
```

---

### Post by dm6257 on 2009-11-08
Thanks.  When I changed from United States server to Main server and reloaded build-essential and b43-fwcutter showed up.

---

