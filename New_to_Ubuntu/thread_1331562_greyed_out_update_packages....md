---
title: "greyed out update packages..."
date: 2009-11-19
forum: New to Ubuntu
---

### Post by mustard greens on 2009-11-19
I have two greyed out update packages ever since upgrade to 9.10.  I assume this means that I did not retain the repositories for them on upgrade, but I cant find where to get them again.

the first package is for adobe-flashplugin version 10.  I am having no trouble viewing flash, but I assume they have made some improvement.

the second is devede DVD creator.  

any help would be appreciated.

---

### Post by cariboo on 2009-11-19
There are more than likely some missing dependencies, give it some time they should show up in the next couple of days.

---

### Post by philinux on 2009-11-19
> **mustard greens said:**
> I have two greyed out update packages ever since upgrade to 9.10.  I assume this means that I did not retain the repositories for them on upgrade, but I cant find where to get them again.

the first package is for adobe-flashplugin version 10.  I am having no trouble viewing flash, but I assume they have made some improvement.

the second is devede DVD creator.  

any help would be appreciated.

Open a terminal, Apps>access>terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any errors in full.

---

### Post by mustard greens on 2009-11-19
> **philinux said:**
> Open a terminal, Apps>access>terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

Post back any errors in full.

 so not exactly an error, but the packages did not upgrade.

Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  adobe-flashplugin devede
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

---

### Post by philinux on 2009-11-19
```
sudo apt-get update && sudo apt-get dist-upgrade
```

Just be careful if it wants to remove anything. Check you're happy.

---

### Post by unequivically on 2009-12-04
Go into synaptic and update from there.  There's installer files that need to be deleted in order to upgrade, and synaptic will do it for you.

---

### Post by mustard greens on 2009-12-04
thank you unequivocally.  that was the fix I needed.  consider this one solved.

---

