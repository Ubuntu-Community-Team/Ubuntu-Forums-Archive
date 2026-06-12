---
title: "Synaptic Package Manager and Update Manager errors"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by crazyk on 2009-04-29
I'm an ubuntu noob.  I'm getting the following error message when I run the Synaptic Package Manage or Update Manager:

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report"

Browsing this board and other boards I attempted the following solution with no luck:

"kevin@ubuntu:~$ sudo dpkg --configure -a && sudo apt-get -f install
[sudo] password for kevin: 
dpkg: parse error, in file `/var/lib/dpkg/updates/0060' near line 1:
 newline in field name `#padding'"

I'm stuck what do I do???

---

### Post by MontelEdwards on 2009-04-29
Why exactly did you do -f install?
Close synaptic, and just run dpkg --configure -a
with sudo of course

---

### Post by crazyk on 2009-04-29
> **monteledwards said:**
> Why exactly did you do -f install?
Close synaptic, and just run dpkg --configure -a
with sudo of course

I tried that, now I get:

 kevin@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0060' near line 1:
 newline in field name `#padding'

---

### Post by crazyk on 2009-04-29
-f install is because i copied a suggested command line.  I really have no idea what it means...

---

### Post by spiderbatdad on 2009-04-29
i would say you can safely remove the file
```
sudo rm /var/lib/dpkg/updates/0060
```

---

### Post by crazyk on 2009-04-29
> **spiderbatdad said:**
> i would say you can safely remove the file
```
sudo rm /var/lib/dpkg/updates/0060
```

That did it!  Thanks a lot!!!O:)

---

### Post by crazyk on 2009-04-29
On second thought I now get this message after running synaptic:

E: /var/cache/apt/archives/linux-headers-2.6.27-11_2.6.27-11.31_all.deb: files list file for package `linux-headers-2.6.27-11' contains empty filename

---

### Post by taurus on 2009-04-29
Maybe you need to clean out the cache first.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by crazyk on 2009-04-29
> **taurus said:**
> Maybe you need to clean out the cache first.

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```


I feel like I'm making progress.  Now I get:

"E: The package linux-headers-2.6.27-11 needs to be reinstalled, but I can't find an archive for it."

I did a partial update and got:

"Remove package in bad state

The package 'linux-headers-2.6.27-11' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?"

I said 'Yes' and then:


The package 'linux-headers-2.6.27-11' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.


So... How do I remove the package from the system?

---

### Post by crazyk on 2009-04-30
So...how do I remove this package in terminal?

---

### Post by spiderbatdad on 2009-04-30
```
sudo apt-get --reinstall linux-headers-2.6.27-11-generic
```

see ```
man apt-get for more details
```Also consider using synaptic package manger to reinstall or fix broken packages.

---

