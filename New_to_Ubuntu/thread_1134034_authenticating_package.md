---
title: "authenticating package"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by deostroll on 2009-04-23
Why is it necessary to authenticate a package? When I did apt-get install gcc g++, somewhere down the line it said, it could not authenticate packages, and prompted me to continue or not...Why is it necessary?

---

### Post by kanikilu on 2009-04-23
It sounds like you added a software source (repository) that is not authenticated. If you post the error message, we can probably track down which repository is causing it, and tell you how to fix it...

---

### Post by deostroll on 2009-04-23
This was the output of the installation I got:
```

deostroll@deostroll-pc:~$ sudo apt-get install gcc g++
[sudo] password for deostroll: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
The following extra packages will be installed:
  cpp-4.3 g++-4.3 gcc-4.3 gcc-4.3-base libgcc1 libgomp1 libstdc++6
  libstdc++6-4.3-dev
Suggested packages:
  gcc-4.3-locales g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg
  gcc-4.3-multilib libmudflap0-4.3-dev libgcc1-dbg libgomp1-dbg
  libmudflap0-dbg libstdc++6-4.3-doc
The following NEW packages will be installed:
  g++ g++-4.3 libstdc++6-4.3-dev
The following packages will be upgraded:
  cpp-4.3 gcc-4.3 gcc-4.3-base libgcc1 libgomp1 libstdc++6
6 upgraded, 3 newly installed, 0 to remove and 280 not upgraded.
Need to get 5484kB/12.0MB of archives.
After this operation, 19.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  gcc-4.3-base libstdc++6 libgomp1 cpp-4.3 gcc-4.3 libgcc1 libstdc++6-4.3-dev
  g++-4.3 g++
Install these packages without verification [y/N]? y
Get:1 http://lk.archive.ubuntu.com intrepid-updates/main libstdc++6-4.3-dev 4.3.2-1ubuntu12 [1354kB]
Err http://lk.archive.ubuntu.com intrepid-updates/main g++-4.3 4.3.2-1ubuntu12 
  Connection failed [IP: 91.189.88.46 80]
Get:2 http://lk.archive.ubuntu.com intrepid/main g++ 4:4.3.1-1ubuntu2 [1444B]
Fetched 1356kB in 11min47s (1916B/s)
Failed to fetch http://lk.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/g++-4.3_4.3.2-1ubuntu12_i386.deb  Connection failed [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


```
How do I know for sure these above packages got installed?

---

### Post by kanikilu on 2009-04-23
Ok, it doesn't look like it's a problem with not having the GPG key for a repository, for example, that would give a different error.

Since it's saying that it can't connect, my first guess would be that the servers you are using are too busy right now. I would probably either wait for the Jaunty rush to die down a bit, or try a different mirror:

How to change the software source in Synaptic:

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download%20Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download%20Server)

---

### Post by deostroll on 2009-04-23
How can I verify if the download actually finished?

---

