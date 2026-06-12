---
title: "the add source is grayed out"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by DarinB on 2009-04-07
when i try to add a source into software sources the add source button stays grayed out as in used the menu to intrepid Display sources.list entries for: intrepid the i copy and paste as below,,,no add source button it is grayed out
This PPA contains the latest debs of Banshee for Ubuntu Gutsy and Hardy. To install Banshee, you must first enable the PPA on your system:
1. Open Software Sources (System->Administration->Software Sources)
2. Navigate to the "Third Party Sources" tab.
3. Click "Add"
4. Enter the APT line below that corresponds to your Ubuntu version that starts with "deb".
5. Click "Add Source"
6. Click "Close"
7. It will prompt you to reload your software cache. Click "Reload".
8. Now install the package "banshee" from Synaptic, or using the command below:
sudo apt-get install banshee

For those who wish to compile from trunk, add the deb-src line and then run "sudo apt-get build-dep banshee-1" to install all required dependencies before starting to compile.

---

### Post by spcwingo on 2009-04-07
I don't know the problem, but you can add it another way.  Press alt+F2 and enter this command:

```
gksu gedit /etc/apt/sources.list
```

At the bottom of this file add the repos' apt line (or lines).  Then save it and open a terminal and type:

```
sudo apt-get update
```

You're now ready to use that repo.

---

### Post by DarinB on 2009-04-08
thanks worked like a charm

---

