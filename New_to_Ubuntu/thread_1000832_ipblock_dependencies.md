---
title: "ipblock dependencies"
date: 2008-12-03
forum: New to Ubuntu
---

### Post by AnonUK on 2008-12-03
I'm trying to use ipblock however it is dependent on these other 2 files.
```

root@anonymous-laptop:~# sudo aptitude install iplist
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  iplist 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 318kB of archives. After unpacking 606kB will be used.
The following packages have unmet dependencies:
  iplist: Depends: libnfnetlink0 (>= 0.0.33) but 0.0.30-2 is installed.
          Depends: libstdc++6 (>= 4.3) but 4.2.4-1ubuntu3 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.
```

However every i've tried to install these and i'm not doing it correctly. 

Can anybody please help?

---

### Post by LowSky on 2008-12-03
first run
```
sudo apt-get update 
```

then run
```
sudo apt-get install libnfnetlink0 libstdc++6 iplist
```

---

### Post by AnonUK on 2008-12-03
> **LowSky said:**
> first run
```
sudo apt-get update 
```

then run
```
sudo apt-get install libnfnetlink0 libstdc++6 iplist
```

Hi thanks

```
root@anonymous-laptop:~# sudo apt-get install libnfnetlink0 libstdc++6 iplist
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnfnetlink0 is already the newest version.
libnfnetlink0 set to manually installed.
libstdc++6 is already the newest version.
Package iplist is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package iplist has no installation candidate
```

I think the dependencies are ok now. However when i try to install iplist via synaptic manager it says

iplist:

Package iplist has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

### Post by mrbig on 2008-12-03
I came across your post when looking for a solution to installing moblock on ubuntu 8.10.

When installing moblock I only got the message about libnfnetlink0.
I found this page where I was able to manually download/install it.
[https://launchpad.net/ubuntu/intrepid/i386/libnfnetlink0-dbg/0.0.33-1](https://launchpad.net/ubuntu/intrepid/i386/libnfnetlink0-dbg/0.0.33-1)
I just downloaded it to the desktop and right-clicked and selected 'Open with "GDebi Package Installer"'. After that moblock installed right away.

Good Luck

oh btw, I checked that other package and mine already has version 2.7 or something, I have all sourced checked in the 'Software Sources'.

Apologies if I sound noobish, I'm relatively new and teaching myself linux =)

Hope I was of some help.

---

### Post by mrbig on 2008-12-03
UPDATE:
After spending the last hour installing different packages I have yet to get the right combination of packages installed to install moblock on ubuntu 8.10.

---

