---
title: "Banjaxed Synaptic"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by kaspar_silas on 2009-03-02
Hi all,

My synaptic is doing strange and worrying things. It started after I installed wu-ftpd by telling me an upgrade of linux-image-2.6.27.13-generic was available. So I clicked install and up popped a message saying I have 3 broken packages. I clicked close, and it went on but then I got a pop up with:

```
E: /var/cache/apt/archives/linux-image-2.6.27-13-generic_2.6.27-13.29_amd64.deb: subprocess pre-installation script returned error exit status 1
```

Hhhm, so I tried running 

$ sudo dpkg --configure -a
$ sudo apt-get update
$ sudo apt-get -f update

these seemed okay so I tried to remove wu-ftpd  which is all that I changed before the madness began.

$ sudo apt-get remove wu-ftpd 

this gave:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  wu-ftpd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 856kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 317809 files and directories currently installed.)
Removing wu-ftpd ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wu-ftpd (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 wu-ftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I get the same thing if I try to install, remove, fix or basically do anything with Synaptic.

Any ideas? No rush by the way as im going home now. Thought I would put it up in case it needs to be pondered over. O im running the 64 bit version of 8.10 if that's important.

Thanks for any help offered.

---

### Post by cariboo on 2009-03-02
Open Synaptic and go to Edit-->Fix Broken Packages, and completely remove the broken packages.

Jim

---

### Post by kaspar_silas on 2009-03-02
Nope the fix package suggestion didn't work. As once the green tick is clicked to apply I get an error reported and I am back to where I started. The same thing if I manually select the packages for complete removal. Or if I do it from the command line.

I tried just about everything. So I thought sod it and used sudo rm to delete all the locked files. eg: 

sudo rm /var/cache/debconf/config.dat 
sudo rm/var/cache/debconf/passwords.dat
etc ...

Then I could, and did, remove the broken packages. Incidentally I tried installing wu-ftpd again just to test. The result was a shafted synaptic again. But deleting the above files seemed to solve it again.

However it was probably a tad cavalier to sudo rm locked files. Especially since I didn't know what they were, nevertheless it seems to be working now. Still if someone could let me know what the files, that got deleted, actually where and their point of existance I would be much oblidged.

All the best

---

### Post by cariboo on 2009-03-02
After you removed the broken packages did you hit the reload button?

Jim

---

### Post by kaspar_silas on 2009-03-03
Yip after I deleted the locked /var files everything worked. Reload, add, remove packages etc. 

I was a bit worried about blindy deleting the files in \var so haven't restarted the computer yet.

---

