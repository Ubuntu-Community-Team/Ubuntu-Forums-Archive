---
title: "'echo' error"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by midgardarts on 2010-02-16
In a likely miss-placed attempt to update open office I have created the following problem when trying to open update manager, package manager or any other install file:

E: Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I am a total beginner with this and I would appreciate hand holding in fixing this, no matter how patronizing or insulting to my intelligence. I am operating a Dell mini-9 with Jaunty 9.04 netbook remix.

Here is the source list:

deb cdrom:[Ubuntu-Netbook-Remix 9.04 _Jaunty Jackalope_ - Release i386 (20090421)]/ jaunty main multiverse restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by mcduck on 2010-02-16
```
E: Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/ppa.list
```

The first line of the **/etc/apt/sources.list.d/ppa.list** -file contains somehting that doesn't belong into that file. Based on the error you have added there a command that you should have actually executed in the terminal. Just remove the extra line, or paste *that* file here and we'll tell you what to remove from it... :)

---

### Post by midgardarts on 2010-02-16
This sounds promising. Here are the contents of the afore mentioned ppa.list file:

echo "#PPA openoffice-pkgs
echo -e echo #PPA openoffice-pkgs
#PPA openoffice-pkgs

---

### Post by mcduck on 2010-02-16
> **midgardarts said:**
> This sounds promising. Here are the contents of the afore mentioned ppa.list file:

echo "#PPA openoffice-pkgs
echo -e echo #PPA openoffice-pkgs
#PPA openoffice-pkgs

that's interesting... *None* of those things should be there, but unlike what I expected that's not a working command for adding a repository either... :)

If those are all the contents in that file, you can simply delete the file. After that run "sudo apt-get update" and things should start working again. Then you can try adding the OpenOffice PPA repository again...

---

### Post by midgardarts on 2010-02-16
My attempts to delete the file failed as It does not think I have permission to do so. Have I missed something in my administrative settings for this?

---

### Post by midgardarts on 2010-02-16
Permission to modify this file is limited to the 'owner', root and I can't seem to change any of it. Is there a way to do this in the console? Although I'm not sure that would get around the permission problem.

---

### Post by midgardarts on 2010-02-16
I think I git it, used the sudo command in the console and then the standard rm to deleate. I'll see if it took.

---

### Post by mcduck on 2010-02-16
That's normal, even admin users don't run with full admin privileges all the time, you have to specifically tell thay you wish to do something as root.

I wonder how you added those lines to that files since that would require exactly the same permissions as removing the file does...

Anyway:
```
sudo rm /etc/apt/sources.list.d/ppa.list
```
or if you want to just edit the file and remove those offending lines:
```
gksudo gedit /etc/apt/sources.list.d/ppa.list
```

..and you might want to read this article about how admin permisisions are handled in Ubuntu: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

