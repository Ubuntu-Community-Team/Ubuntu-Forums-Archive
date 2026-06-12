---
title: "Apache2 installing problem"
date: 2011-08-27
forum: New to Ubuntu
---

### Post by NabiVakili on 2011-08-27
I want to install Apache2 on Ubuntu 10.04,
I used this command :
> sudo apt-get install apache2

but I got this error:
> 
package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package apache2


I checked the source.list file, there are some universe repositories :
> 
#
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted

#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe


What is the problem?

---

### Post by snip3r8 on 2011-08-27
have you updated your apt lists?

```
sudo apt-get update
```

---

### Post by madhater on 2011-08-27
The problem will be because of an incomplete /etc/apt/sources.list file. I advise you look at this article:

[http://www.mindtrickz.org/blog/default-sources-list-file-in-ubuntu-11-04/](http://www.mindtrickz.org/blog/default-sources-list-file-in-ubuntu-11-04/)

it shows the default sources.list file. Make sure your /etc/apt/sources.list file is complete and then run:

```
 sudo apt-get update 
```This should fix the problem. From what you have told me, you do not have the complete sources.list file. 

After this make sure you have all the repository enabled all the software sources. You can edit this via synaptic package manager. In synaptic, go: Settings > Repositories 


madhater

---

### Post by NabiVakili on 2011-08-27
I used that command and it fixed the problem.
after updating lists, I can install every needed package using "apt-get install"

Thank you for your help

---

