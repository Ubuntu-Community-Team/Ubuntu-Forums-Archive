---
title: "Get rid of rekonq"
date: 2010-12-07
forum: New to Ubuntu
---

### Post by JP121 on 2010-12-07
Hi.

I have Kubuntu and want to get rid of rekonq, because I have replaced it with Chromium.  When I try to apt-get purge it, apt-get tries to add konqueror, too.  How do I get rid of it without adding konqueror?

Thanks.

---

### Post by cf0531 on 2010-12-07
cant you just remove it in the package manager?

---

### Post by JP121 on 2010-12-07
Nope.  Package manager wants to do the same thing.

---

### Post by NightwishFan on 2010-12-07
Try:
```
sudo apt-get --no-install-recommends remove rekonq
```

---

### Post by JP121 on 2010-12-07
> **NightwishFan said:**
> Try:
```
sudo apt-get --no-install-recommends remove rekonq
```
same thing happened as last time.  apt-get wants to install two new packages.

For what it's worth.  Here's the response apt-get gives.

```
sudo apt-get --no-install-recommends remove rekonq
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  konqueror libkonqsidebarplugin4a
Suggested packages:
  konq-plugins
Recommended packages:
  konqueror-nsplugins
The following packages will be REMOVED:
  kubuntu-konqueror-shortcuts rekonq
The following NEW packages will be installed:
  konqueror libkonqsidebarplugin4a
0 upgraded, 2 newly installed, 2 to remove and 1 not upgraded.
Need to get 1,051kB of archives.
After this operation, 1,380kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

---

### Post by NightwishFan on 2010-12-07
I wish I could test this, my connection is too slow to install a bunch of KDE stuff. :(

If worst comes to worst just let it run, and then just remove the packages after.

---

### Post by JP121 on 2010-12-07
Yeah, I probably am just gonna have to let it stay.  It seems interesting that it won't let you just rid of the darn thing.

---

### Post by NightwishFan on 2010-12-07
I see from the output you specified it seems like they are only meta-packages. Just let the command finish, and see if it works. "1,051kB" total is not enough unless almost all of Konqueror is already installed. Then just run:

```
sudo apt-get remove konqueror
```

---

### Post by JP121 on 2010-12-07
> **NightwishFan said:**
> I see from the output you specified it seems like they are only meta-packages. Just let the command finish, and see if it works. "1,051kB" total is not enough unless almost all of Konqueror is already installed. Then just run:

```
sudo apt-get remove konqueror
```

That worked.  Neither rekonq nor konqueror show up, and I think I got rid of of all the unneeded dependencies.  Thanks a ton.

---

### Post by NightwishFan on 2010-12-07
No problem, have fun. :)

---

