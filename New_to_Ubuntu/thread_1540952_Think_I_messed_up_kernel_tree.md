---
title: "Think I messed up kernel tree"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by generic41209 on 2010-07-28
Hi all,
      I was trying to compile a debian package, and I definitely messed something up in the process.

      I can no longer install programs using the Ubuntu Software Center, Here's what I get:
```
installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 212950 files and directories currently installed.) 
Removing bitpim ... 
Processing triggers for menu ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up advdaq (1.06.0001) ... 
ln: target `libadvdaq.so' is not a directory 
dpkg: error processing advdaq (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 advdaq 
Setting up advdaq (1.06.0001) ... 
ln: target `libadvdaq.so' is not a directory 
dpkg: error processing advdaq (--configure): 
 subprocess installed post-installation script returned error exit status 1 
```As you can see, I changed something that points the system to advdaq, and libadvdaq.so, etc. (advdaq is what I was trying to compile)

---

