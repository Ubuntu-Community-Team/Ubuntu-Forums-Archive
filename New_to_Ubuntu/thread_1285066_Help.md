---
title: "Help"
date: 2009-10-07
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-07
I tried to download Cairo Dock without really knowing what I was doing. I now have a problem. When I go to Synaptic Package manager I get the following message. How do I carry out this instruction please and any advice about downloading Cairo Dock will also be welcome.:confused:

E: Type ‘sudo’ is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

---

### Post by BQAggie2006 on 2009-10-07
It appears that you have copied and pasted something incorrectly into your sources.list file (specifically sudo on line 56). Could you please paste the output of 
```
cat /etc/apt/sources.list
```from the command line and we can try to help you with your issue.

---

### Post by fixerman on 2009-10-07
> **BQAggie2006 said:**
> It appears that you have copied and pasted something incorrectly into your sources.list file (specifically sudo on line 56). Could you please paste the output of 
```
cat /etc/apt/sources.list
```from the command line and we can help you fix your problem.

This is what I got.

patrick@patrick-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates restricted main
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock # For Ubuntu 9.04

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

patrick@patrick-desktop:~$

---

### Post by howefield on 2009-10-07
Remove the last two lines that read

```
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins
```

These are terminal commands, not for adding to your sources.list

---

### Post by BQAggie2006 on 2009-10-07
Okay, you will need to edit your /etc/apt/sources.list file and remove the following lines from the bottom:

> 
sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-insYou can either edit the file in a non-graphical editor with the following command:

```
sudo nano /etc/apt/sources.list
```or in a graphical editor with this command:

```
gksudo gedit /etc/apt/sources.list
```Once you have the file open in either editor, remove those lines I posted above and save the file. Those lines are the actual commands you need to install cairo-dock after you have edited your sources file.

---

### Post by fixerman on 2009-10-07
Thanks folks. I managed that eventually. Any advice on down loading and installing Cairo Dock?

---

### Post by howefield on 2009-10-07
> **fixerman said:**
> Thanks folks. I managed that eventually. Any advice on down loading and installing Cairo Dock?

Use Synaptic Package Manager, I think it was included in the repositories from Jaunty onwards.

[http://packages.ubuntu.com/search?keywords=cairo-dock](http://packages.ubuntu.com/search?keywords=cairo-dock)

---

### Post by fabounet on 2009-10-08
please don't use the Ubuntu repository, as the version is really outdated.
see the wiki.
I think you've already added the Cairo-Dock's repository, so now just type
```
sudo apt-get install cairo-dock cairo-dock-plug-ins
```
in a terminal, or use Synaptic.

---

### Post by fixerman on 2009-10-08
Thanks folks for all your advice! All sorted now! I'm really looking forward to using and becoming more efficient with my new OS. No doubt I shall be back from time to time to pick your brains.

Thanks again!:P

---

### Post by 3rdalbum on 2009-10-08
In future, don't add lines directly to the sources.list. The Software Sources program (System > Administration > Software Sources) can help you add a line to sources.list, and will not add the line unless it uses the correct syntax. This prevents that sort of error from happening.

---

