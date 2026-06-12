---
title: "Broken Dependencies/Packages"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by wind_dragon on 2009-02-03
After the latest install of updates something went wrong not sure what. but I think it affected my flash plugin. When I get on youtube and watch a video it asks me if i want to abort because there is a script thats acting weird and stuff. I tried to reinstall it but got an error about broken dependencies.
I did the "sudo apt-get install -f":

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-image-2.6.24-23-generic
Suggested packages:
  linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
  linux-image-2.6.24-23-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/18.4MB of archives.
After this operation, 61.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--unpack):
 files list file for package `myspell-en-gb' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I'm not sure what to do next though? :(

---

### Post by handydan918 on 2009-02-03
What did ```
sudo apt-get install -f
```give you? any errors?

You might try ```
sudo dpkg --configure -a
```

---

### Post by wind_dragon on 2009-02-03
> **handydan918 said:**
> What did ```
sudo apt-get install -f
```give you? any errors?

You might try ```
sudo dpkg --configure -a
```

this what i got for sudo dpkg --configure -a:
```
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-23-generic:
 linux-restricted-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
dpkg: error processing linux-restricted-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-23-generic:
 linux-ubuntu-modules-2.6.24-23-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
dpkg: error processing linux-ubuntu-modules-2.6.24-23-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-23-generic; however:
  Package linux-image-2.6.24-23-generic is not installed.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-23-generic; however:
  Package linux-ubuntu-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-23-generic; however:
  Package linux-restricted-modules-2.6.24-23-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.23.25); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.23.25); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-restricted-modules-2.6.24-23-generic
 linux-ubuntu-modules-2.6.24-23-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic

```
The sudo apt-get install -f gave me:

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
linux-image-2.6.24-23-generic
Suggested packages:
linux-doc-2.6.24 linux-source-2.6.24
The following NEW packages will be installed:
linux-image-2.6.24-23-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B/18.4MB of archives.
After this operation, 61.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb (--unpack):
files list file for package `myspell-en-gb' is missing final newline
Errors were encountered while processing:
/var/cache/apt/archives/linux-image-2.6.24-23-generic_2.6.24-23.48_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by pdtpatrick on 2009-02-03
see if you can just reinstall the flash package. 

sudo apt-get install ubuntu-restricted-extras

---

### Post by wind_dragon on 2009-02-03
no dice. It gave me the same error and said i should run:
```
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```
which i did, but ended up with
```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

---

### Post by wind_dragon on 2009-02-13
I recently found out (after snooping around in the package) that I have 3 broken packages.
1. linux-image-generic
2. linux-restricted-modules-2.6.24-23-generic
3. linux-ubuntu-modules-2.6.24-23-generic

I tried to reinstall them but got this error
```
E: linux-generic: files list file for package `myspell-en-gb' is missing final newline

```
I tried to remove them and got the same error. I then proceeded to completely remove them but got the same error.:(

---

### Post by wind_dragon on 2009-02-15
bump

---

### Post by neu2buntu on 2009-02-15
there is an option in synaptic to "fix broken packages" it is in the "edit" tab, failing this open a terminal and type ```
man apt-get
```  this will show you the manual for apt-get..  i see there is a "--fix-broken" option im not 100% sure how to run this command it may be along the lines of ```
sudo apt-get install NAME OF PACKAGES --fix-broken
```

---

