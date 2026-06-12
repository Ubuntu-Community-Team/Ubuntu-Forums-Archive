---
title: "[SOLVED] cant remove some packages"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by linuxnovice on 2008-12-11
Hi,

I am not sure what I messed up. But for the past couple of days, I have a couple of packages which I cant remove nor can I upgrade them. When I run apt-get remove this is what I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gettext (0.17-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
Setting up slib (3a4-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib
E: Sub-process /usr/bin/dpkg returned an error code (1)

The packages in question are gettext and slib. I cant seem to remove them nor do I know what they are for.

This is what I get when I run apt-get remove on these packages:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  gettext slib
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 11.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128992 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing slib ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks.

---

### Post by zvacet on 2008-12-11
```
sudo dpkg --configure -a
```

---

### Post by cariboo on 2008-12-11
Try System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

JIm

---

### Post by linuxnovice on 2008-12-11
> Try System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages.

JIm 

I am running Kubuntu 8.04.

> **zvacet said:**
> ```
sudo dpkg --configure -a
```

I ran that command. Then tried to remove both the packages but got the same errors:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  gettext slib
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 11.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128992 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing slib ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by LowSky on 2008-12-11
```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
sudo apt-get remove gettext slib
```

if that dont work force it

```
sudo apt-get -f remove gettext slib
```

---

### Post by rhcm123 on 2008-12-11
> **linuxnovice said:**
> Hi,

I am not sure what I messed up. But for the past couple of days, I have a couple of packages which I cant remove nor can I upgrade them. When I run apt-get remove this is what I get:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gettext (0.17-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
Setting up slib (3a4-4) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib
E: Sub-process /usr/bin/dpkg returned an error code (1)

The packages in question are gettext and slib. I cant seem to remove them nor do I know what they are for.

This is what I get when I run apt-get remove on these packages:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  gettext slib
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 11.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128992 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing slib ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib
E: Sub-process /usr/bin/dpkg returned an error code (1)

Thanks.

Are they dependancies? dpkg might be keeping them because somthing else needs them. Unless you are really short on space, i would just keep them.

---

### Post by zvacet on 2008-12-11
```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

### Post by linuxnovice on 2008-12-12
> **LowSky said:**
> ```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
sudo apt-get remove gettext slib
```

if that dont work force it

```
sudo apt-get -f remove gettext slib
```

Nope that didnt work. Gave me same error again.

> Are they dependancies? dpkg might be keeping them because somthing else needs them. Unless you are really short on space, i would just keep them.

I dont know what they are. Everytime I do an apt-get upgrade it gives me those errors which is really frustrating.

> **zvacet said:**
> ```
sudo dpkg --remove --force-remove-reinstreq package_name
```

I got pretty much the same error again.

(Reading database ... 128992 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing slib ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib

---

### Post by rhcm123 on 2008-12-12
> **linuxnovice said:**
> Nope that didnt work. Gave me same error again.



I dont know what they are. Everytime I do an apt-get upgrade it gives me those errors which is really frustrating.



I got pretty much the same error again.

(Reading database ... 128992 files and directories currently installed.)
Removing gettext ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--remove):
 subprocess pre-removal script returned error exit status 1
install-info: No dir file specified; try --help for more information.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Removing slib ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing slib (--remove):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 gettext
 slib

The -f option on apt does not force the action, instead it tries to fix broken dependencies. Since it didn't work, it isn't dependency.

Run the following two commands:
```
sudo apt-get check
sudo apt-get remove -v gettext

```
The top command checks your dependencies
the bottom tries to remove with verbose output, so we can see more indepth of the problem

---

### Post by linuxnovice on 2008-12-13
> **rhcm123 said:**
> The -f option on apt does not force the action, instead it tries to fix broken dependencies. Since it didn't work, it isn't dependency.

Run the following two commands:
```
sudo apt-get check
sudo apt-get remove -v gettext

```
The top command checks your dependencies
the bottom tries to remove with verbose output, so we can see more indepth of the problem

Umm..I ran the commands and I got this output:

> apt 0.7.9ubuntu17.1 for i386 compiled on Oct 27 2008 18:11:08
Supported modules:
*Ver: Standard .deb
*Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian Translation Index
 Idx: Debian dpkg status file


I am not sure whether it provides any useful info though. Of coursem I am still learning new things in linux....

---

### Post by rhcm123 on 2008-12-15
> **linuxnovice said:**
> Umm..I ran the commands and I got this output:



I am not sure whether it provides any useful info though. Of coursem I am still learning new things in linux....

Crap. -v just does version numbers, oops. I hate APT some times. Here we go again.

This is a long shot, but try reconfiguring dpkg (sudo dkpg-reconfigure dpkg). 

If it dosent work, you can try the very dangerous options. If you want to, and are sure about this, then try reinstalling it:
```
sudo apt-get remove dpkg
(ignore any complaints about dependacies)
sudo apt-get install dpkg
```

---

### Post by Ender41 on 2008-12-15
> **rhcm123 said:**
> Crap. -v just does version numbers, oops. I hate APT some times. Here we go again.

This is a long shot, but try reconfiguring dpkg (sudo dkpg-reconfigure dpkg). 

If it dosent work, you can try the very dangerous options. If you want to, and are sure about this, then try reinstalling it:
```
sudo apt-get remove dpkg
(ignore any complaints about dependacies)
sudo apt-get install dpkg
```

I would try sudo apt-get install -f 
first, if that doesn't fix them then try apt-get remove the entire name of the package rather than slib or whatever.
To find out what it is called
sudo dpkg -l | grep slib
in my case that package is called e2fslibs, note taking this one out can cause some real breaks of the system.

---

### Post by linuxnovice on 2008-12-16
> **Ender41 said:**
> I would try sudo apt-get install -f 
first, if that doesn't fix them then try apt-get remove the entire name of the package rather than slib or whatever.
To find out what it is called
sudo dpkg -l | grep slib
in my case that package is called e2fslibs, note taking this one out can cause some real breaks of the system.

I got the same thing when I ran that. For gettext I got this:

```
rF  gettext                                    0.17-2ubuntu1                                              GNU Internationalization utilities
ii  gettext-base                               0.17-2ubuntu1                                              GNU Internationalization utilities for the base system
ii  liblocale-gettext-perl                     1.05-2ubuntu1                                              Using libc functions for internationalization in Perl

```

Its not that I want to remove these packages. I just wish those errors of processing dont appear each time I run apt-get. Either way, until I can figure out why those errors are appearing I dont think I will remove anything.

Thanks.

---

### Post by Ender41 on 2008-12-16
> **linuxnovice said:**
> I got the same thing when I ran that. For gettext I got this:

```
rF  gettext                                    0.17-2ubuntu1                                              GNU Internationalization utilities
ii  gettext-base                               0.17-2ubuntu1                                              GNU Internationalization utilities for the base system
ii  liblocale-gettext-perl                     1.05-2ubuntu1                                              Using libc functions for internationalization in Perl

```

Its not that I want to remove these packages. I just wish those errors of processing dont appear each time I run apt-get. Either way, until I can figure out why those errors are appearing I dont think I will remove anything.

Thanks.

  What is the output from sudo apt-get install -f
It might be that you need to go back and forth a few times, it is also possible that one of the packages was corrupted, cd to /var/cache/apt/archives
  This is where all your downloaded packages are downloaded to you might be able to fix things with sudo dpkg -i the packages, you might need to put several in the line due to dependencies.

---

### Post by rhcm123 on 2008-12-16
> **Ender41 said:**
> I would try sudo apt-get install -f 
first, if that doesn't fix them then try apt-get remove the entire name of the package rather than slib or whatever.
To find out what it is called
sudo dpkg -l | grep slib
in my case that package is called e2fslibs, note taking this one out can cause some real breaks of the system.

-f does fix the dependencies, as I just checked:
```
  -f  Attempt to correct a system with broken dependencies in place

```
and he already ran it and it didn't work. 

This seems to have corrupted dpkg, not the packages... hmm...

---

### Post by linuxnovice on 2008-12-17
> **Ender41 said:**
> What is the output from sudo apt-get install -f
It might be that you need to go back and forth a few times, it is also possible that one of the packages was corrupted, cd to /var/cache/apt/archives
  This is where all your downloaded packages are downloaded to you might be able to fix things with sudo dpkg -i the packages, you might need to put several in the line due to dependencies.

I dont know whether this is weird or not. Here are the contents of /var/cache/apt/archives:
lock partial

partial is an empty directory. And lock is some file I dont know about.

Thanks.

---

### Post by rhcm123 on 2008-12-19
> **linuxnovice said:**
> I dont know whether this is weird or not. Here are the contents of /var/cache/apt/archives:
lock partial

partial is an empty directory. And lock is some file I dont know about.

Thanks.

Lock is a very important file, don't touch it. Lock is used to ensure root access (to make sure that root is the only one using apt) and to also make sure that 2 apt processes aren't running at the same time, which can screw up dependenies. It contains nothing, it just exists to make sure the user has proper permissions.

Partial is used for packages being downloaded that haven't completed.

You should have several recently downloaded packages in /archives. But, since you ran apt-get clean/autoclean, it's to be expeceted that it's empty. I havent run auto clean in a while, so i have smbfs and di in my directory.

Hm... this is edging closer and closer to a "you have to reinstall" solution.

---

### Post by linuxnovice on 2008-12-21
Well, it doesnt really hurt me in anyway other than being an irritant. So I am just going to ignore it now. I have a lot of stuff configured and all my school/reserach work here. I dont have the time to go with a reinstall right now..so I'll just ignore it. Thanks anyway guys.

---

### Post by rhcm123 on 2008-12-24
> **linuxnovice said:**
> Well, it doesnt really hurt me in anyway other than being an irritant. So I am just going to ignore it now. I have a lot of stuff configured and all my school/reserach work here. I dont have the time to go with a reinstall right now..so I'll just ignore it. Thanks anyway guys.

alright, but I may warn you that this is becoming a "you have to reinstall" solution... this is one of the strangest things i have encountered in a while

---

### Post by linuxnovice on 2008-12-30
Ok I reinstalled my system. This time I installed Ubuntu 8.04 and everything was going fine until a few moments ago. Same type of error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gnupg2 (2.0.7-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gnupg2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 gnupg2
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am pretty sure that I did not break anything. What the hell is going on?

---

### Post by linuxnovice on 2008-12-30
If its of any help, this problem occured after I unsuccessfully tried to install acetoneiso2 which is not in the repositories.

Thanks.

---

### Post by oldos2er on 2008-12-30
How did you try to install acetone?

---

### Post by linuxnovice on 2008-12-30
> **oldos2er said:**
> How did you try to install acetone?


I got the deb package from there site here: [http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_20080508-1_i386.deb?modtime=1210292307&big_mirror=0](http://downloads.sourceforge.net/acetoneiso2/acetoneiso2_20080508-1_i386.deb?modtime=1210292307&big_mirror=0)

Anyway, the latest is I tried to install CVS (apt-get install cvs) and it ended up giving me an error too:

```
Setting up cvs (1:1.12.13-9) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing cvs (--configure):
 subprocess post-installation script returned error exit status 1
Setting up gnupg2 (2.0.7-1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gnupg2 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cvs
 gnupg2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Am I doing something very very wrong?

---

### Post by linuxnovice on 2008-12-30
Ok another update. I wanted to install vmware-player. So I followed the instructions given here: [https://help.ubuntu.com/community/VMware/Player#Creating%20Virtual%20Machine%20installations](https://help.ubuntu.com/community/VMware/Player#Creating%20Virtual%20Machine%20installations)

And this is what I got:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gettext (0.17-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of intltool-debian:
 intltool-debian depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing intltool-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of po-debconf:
 po-debconf depends on gettext (>= 0.16); however:
  Package gettext is not configured yet.
 po-debconf depends on intltool-debian (>= 0.34.2+20060512); however:
  Package intltool-debian is not configured yet.
dpkg: error processing po-debconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on po-debconf; however:
  Package po-debconf is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-package:
 kernel-package depends on po-debconf; however:
  Package po-debconf is not configured yet.
 kernel-package depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing kernel-package (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-wedge:
 kernel-wedge depends on debhelper (>= 4.2); however:
  Package debhelper is not configured yet.
dpkg: error processing kernel-wedge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-kernel-devel:
 linux-kernel-devel depends on debhelper; however:
  Package debhelper is not configured yet.
 linux-kernel-devel depends on kernel-package; however:
  Package kernel-package is not configured yet.
 linux-kernel-devel depends on kernel-wedge; however:
  Package kernel-wedge is not configured yet.
dpkg: error processing linux-kernel-devel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gettext
 intltool-debian
 po-debconf
 debhelper
 kernel-package
 kernel-wedge
 linux-kernel-devel
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is anyone else having same/similar problems?

---

### Post by oldos2er on 2008-12-30
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by decoherence on 2008-12-30
your errors point to a problem with the program install-info

please post output of the following

```
which install-info
locate install-info
```

this is a real bummer since almost nobody (especially in ubuntu) makes use of the info system anyway...

---

### Post by Norm24 on 2008-12-30
How about this:

```
sudo apt-get autoremove
```

Very surprised no one suggested this.

---

### Post by decoherence on 2008-12-30
> **Norm24 said:**
> How about this:

```
sudo apt-get autoremove
```

Very surprised no one suggested this.

The posted dpkg output indicates there aren't any packages that would be affected by autoremove.

---

### Post by linuxnovice on 2008-12-30
Yes. I tried everything sudo apt-get autoremove, sudo apt-get -f install. Same errors.

---

### Post by linuxnovice on 2008-12-30
> **oldos2er said:**
> Can you please post the output of "cat /etc/apt/sources.list"?

sources.list:

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu hardy partner
 deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

> decoherence  	
Re: cant remove some packages
your errors point to a problem with the program install-info

please post output of the following

Code:

which install-info
locate install-info

this is a real bummer since almost nobody (especially in ubuntu) makes use of the info system anyway... 

which install-info:

```
/usr/local/bin/install-info

```

locate install-info:

```
/usr/local/bin/install-info
/usr/local/share/man/man1/install-info.1
/usr/local/share/man/man1/install-info.pdf
/usr/local/texlive/2008/bin/i386-linux/install-info
/usr/local/texlive/2008/texmf/doc/man/man1/install-info.1
/usr/local/texlive/2008/texmf/doc/man/man1/install-info.pdf
/usr/sbin/install-info
/usr/share/man/de/man8/install-info.8.gz
/usr/share/man/fr/man8/install-info.8.gz
/usr/share/man/man8/install-info.8.gz
/usr/share/man/sv/man8/install-info.8.gz

```

What is install-info anyway?

Thanks.

---

### Post by mc4man on 2008-12-30
> What is install-info anyway

It's a shell script that's installed with dpkg to /usr/sbin

Odd you show one in /usr/local/bin also

---

### Post by linuxnovice on 2008-12-30
> **mc4man said:**
> It's a shell script that's installed with dpkg to /usr/sbin

Odd you show one in /usr/local/bin also

Where would it normally be?

---

### Post by decoherence on 2008-12-30
> **linuxnovice said:**
> sources.list:
which install-info:

```
/usr/local/bin/install-info

```

locate install-info:

```
/usr/local/bin/install-info
/usr/local/share/man/man1/install-info.1
/usr/local/share/man/man1/install-info.pdf
/usr/local/texlive/2008/bin/i386-linux/install-info
/usr/local/texlive/2008/texmf/doc/man/man1/install-info.1
/usr/local/texlive/2008/texmf/doc/man/man1/install-info.pdf
/usr/sbin/install-info
/usr/share/man/de/man8/install-info.8.gz
/usr/share/man/fr/man8/install-info.8.gz
/usr/share/man/man8/install-info.8.gz
/usr/share/man/sv/man8/install-info.8.gz

```

What is install-info anyway?

Thanks.

I'm fairly certain this is your problem. I suspect your non-repository program installed another version of install-info (/usr/local/bin/install-info) which is getting called instead of the right one (/usr/sbin/install-info)

The output of the following might give us more clues as to where this install-info came from
```

ls -l `which install-info`
```

in the mean time, it can't hurt to run
```

source .profile
```

and try installing/removing/whatever again.

as I understand, install-info adds/updates entries for installed software to the Info documentation system, which is GNU's failed attempt (imho) at replacing the "man" manual system. The idea is that you type "info whatever" where whatever is the program you installed. Like typing "man whatever" only more of a PITA.

---

### Post by linuxnovice on 2008-12-30
> **decoherence said:**
> I'm fairly certain this is your problem. I suspect your non-repository program installed another version of install-info (/usr/local/bin/install-info) which is getting called instead of the right one (/usr/sbin/install-info)

The output of the following might give us more clues as to where this install-info came from
```

ls -l `which install-info`
```

in the mean time, it can't hurt to run
```

source .profile
```

and try installing/removing/whatever again.

as I understand, install-info adds/updates entries for installed software to the Info documentation system, which is GNU's failed attempt (imho) at replacing the "man" manual system.


Hey thanks. 

ls -l `which install-info`:

```
lrwxrwxrwx 1 root root 51 2008-12-30 11:26 /usr/local/bin/install-info -> /usr/local/texlive/2008/bin/i386-linux/install-info

```

It seems to be symbolically linked..which means they both are the same thing right (like a shortcut)?

Ok I did a source .profile and apt-get upgrade. No difference..same errors.

Thanks for your help.

---

### Post by mc4man on 2008-12-30
A quick test shows it doesn't matter where install-info is. If it's not found the error message would be different. (install-info not found on path

---

### Post by decoherence on 2008-12-30
> A quick test shows it doesn't matter where install-info is. If it's not found the error message would be different. (install-info not found on path

it matters if the texlive version of install-info works differently than the one in /usr/sbin/install-info. this issue has struck other users, but long ago. i wonder if there is a regression with tetex? i'm trying to reproduce the problem now.

i wonder why tetex installs its own version of install-info?

i'll get back to you, linuxnovice...

---

### Post by linuxnovice on 2008-12-30
> **decoherence said:**
> it matters if the texlive version of install-info works differently than the one in /usr/sbin/install-info. this issue has struck other users, but long ago. i wonder if there is a regression with tetex? i'm trying to reproduce the problem now.

i wonder why tetex installs its own version of install-info?

i'll get back to you, linuxnovice...

I am still not sure about the install-info stuff. But I did not install texlive using tetex in the repositories. I used the internet installer from the TUG (texlive users group) on their website. [http://www.tug.org/texlive/acquire.html](http://www.tug.org/texlive/acquire.html)

I just ran it with root permission and accepted the defaults.

Thanks for your help!

---

### Post by mc4man on 2008-12-30
Try this one after the other (I know you've tried some, do all of them

```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install cvs
```

Note: the one installed in /usr/local/sbin will be 'accessed' first over /usr/sbin (meaning install-info

---

### Post by linuxnovice on 2008-12-30
> **mc4man said:**
> Try this one after the other (I know you've tried some, do all of them

```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get install cvs
```

Note: the one installed in /usr/local/sbin will be 'accessed' first over /usr/sbin (meaning install-info

Ok I just put them all in one script and ran it:

```
configure -a
Setting up gettext (0.17-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of intltool-debian:
 intltool-debian depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing intltool-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-package:
 kernel-package depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing kernel-package (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-kernel-devel:
 linux-kernel-devel depends on kernel-package; however:
  Package kernel-package is not configured yet.
dpkg: error processing linux-kernel-devel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of po-debconf:
 po-debconf depends on gettext (>= 0.16); however:
  Package gettext is not configured yet.
 po-debconf depends on intltool-debian (>= 0.34.2+20060512); however:
  Package intltool-debian is not configured yet.
dpkg: error processing po-debconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on po-debconf; however:
  Package po-debconf is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-wedge:
 kernel-wedge depends on debhelper (>= 4.2); however:
  Package debhelper is not configured yet.
dpkg: error processing kernel-wedge (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gettext
 intltool-debian
 kernel-package
 linux-kernel-devel
 po-debconf
 debhelper
 kernel-wedge

apt-get clean

apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

apt-get update
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US                                       
Hit http://archive.canonical.com hardy Release.gpg                                                  
Ign http://archive.canonical.com hardy/partner Translation-en_US                                     
Hit http://security.ubuntu.com hardy-security Release.gpg                                            
Ign http://security.ubuntu.com hardy-security/main Translation-en_US                                                       
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US                                                 
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US                                                        
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US                                                          
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US  
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg           
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.canonical.com hardy Release                                             
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US                   
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release                
Hit http://us.archive.ubuntu.com hardy Release                                            
Hit http://packages.medibuntu.org hardy Release.gpg                                                             
Hit http://archive.canonical.com hardy/partner Packages                                                                                         
Hit http://security.ubuntu.com hardy-security/main Packages                                                                
Hit http://us.archive.ubuntu.com hardy-updates Release                                               
Hit http://archive.canonical.com hardy/partner Sources                                                                                          
Hit http://security.ubuntu.com hardy-security/restricted Packages                                                          
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/restricted Sources     
Hit http://security.ubuntu.com hardy-security/universe Packages      
Hit http://us.archive.ubuntu.com hardy/main Packages                 
Hit http://us.archive.ubuntu.com hardy/restricted Packages           
Hit http://us.archive.ubuntu.com hardy/main Sources                  
Hit http://us.archive.ubuntu.com hardy/restricted Sources            
Hit http://us.archive.ubuntu.com hardy/universe Packages             
Ign http://packages.medibuntu.org hardy/free Translation-en_US       
Hit http://security.ubuntu.com hardy-security/universe Sources       
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Hit http://us.archive.ubuntu.com hardy/universe Sources                        
Hit http://us.archive.ubuntu.com hardy/multiverse Packages                     
Hit http://us.archive.ubuntu.com hardy/multiverse Sources                      
Hit http://us.archive.ubuntu.com hardy-updates/main Packages                   
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages             
Hit http://us.archive.ubuntu.com hardy-updates/main Sources                    
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources              
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages               
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources                
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages             
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Hit http://packages.medibuntu.org hardy/free Packages
Hit http://packages.medibuntu.org hardy/non-free Packages
Reading package lists... Done

cvs install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cvs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gettext (0.17-2ubuntu1) ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of intltool-debian:
 intltool-debian depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing intltool-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of po-debconf:
 po-debconf depends on gettext (>= 0.16); however:
  Package gettext is not configured yet.
 po-debconf depends on intltool-debian (>= 0.34.2+20060512); however:
  Package intltool-debian is not configured yet.
dpkg: error processing po-debconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on po-debconf; however:
  Package po-debconf is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-package:
 kernel-package depends on po-debconf; however:
  Package po-debconf is not configured yet.
 kernel-package depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing kernel-package (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kernel-wedge:
 kernel-wedge depends on debhelper (>= 4.2); however:
  Package debhelper is not configured yet.
dpkg: error processing kernel-wedge (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-kernel-devel:
 linux-kernel-devel depends on debhelper; however:
  Package debhelper is not configured yet.
 linux-kernel-devel depends on kernel-package; however:
  Package kernel-package is not configured yet.
 linux-kernel-devel depends on kernel-wedge; however:
  Package kernel-wedge is not configured yet.
dpkg: error processing linux-kernel-devel (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gettext
 intltool-debian
 po-debconf
 debhelper
 kernel-package
 kernel-wedge
 linux-kernel-devel
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by decoherence on 2008-12-30
> **linuxnovice said:**
> I am still not sure about the install-info stuff. But I did not install texlive using tetex in the repositories. I used the internet installer from the TUG (texlive users group) on their website. [http://www.tug.org/texlive/acquire.html](http://www.tug.org/texlive/acquire.html)

I just ran it with root permission and accepted the defaults.

Thanks for your help!

I think we found your problem. I'll continue installing the one from the repo just to confirm that it isn't a problem there.

[http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html)

i note they 'strongly' suggest not running the installer as root. i wonder if this is why? if the installer can't run as root, it will likely put this install-info binary under your home directory, in which case it will not interfere with dpkg because linux will find /usr/sbin/install-info before it finds ~/bin/install-info (or wherever it installs it when it doesn't have root)

i'm not really familiar with this software, so i'm not totally sure about this, but based on this information it's my best guess. not being familiar with it, i also can't really help with specifics. I suggest getting in touch with someone from TUG. maybe reference this thread and see if they can suggest something.

good luck!

---

### Post by linuxnovice on 2008-12-30
> **decoherence said:**
> I think we found your problem. I'll continue installing the one from the repo just to confirm that it isn't a problem there.

[http://www.tug.org/texlive/quickinstall.html](http://www.tug.org/texlive/quickinstall.html)

i note they 'strongly' suggest not running the installer as root. i wonder if this is why? if the installer can't run as root, it will likely put this install-info binary under your home directory, in which case it will not interfere with dpkg because linux will find /usr/sbin/install-info before it finds ~/bin/install-info (or wherever it installs it when it doesn't have root)

i'm not really familiar with this software, so i'm not totally sure about this, but based on this information it's my best guess. not being familiar with it, i also can't really help with specifics. I suggest getting in touch with someone from TUG. maybe reference this thread and see if they can suggest something.

good luck!

I ran it as root so that it could make sym link all the binaries to /usr/local/bin. I guess I could easily have added their binary path to my PATH...

Anyway, would it help if I just delete the install-info in texlive?

---

### Post by decoherence on 2008-12-30
> **linuxnovice said:**
> I ran it as root so that it could make sym link all the binaries to /usr/local/bin. I guess I could easily have added their binary path to my PATH...

Anyway, would it help if I just delete the install-info in texlive?

it might break texlive, but if i'm right it should fix dpkg/apt.

rather than delete it, try something more temporary

```
chmod -x /usr/local/bin/install-info
```

that will keep it from running and ubuntu should move on to the next, proper install-info. if everything goes kablooey, you can reverse it with

```
chmod +x /usr/local/bin/install-info
```

let us know!

PS if they suggest running the installer as non-root then I would tend to assume (perhaps incorrectly) that they will add the location of whatever binaries they install to your path for you. if they don't then their instruction should explicitly tell you to add the location to the path.

if neither of these are the case, i'd report a usability bug to whomever maintains it.

---

### Post by linuxnovice on 2008-12-30
> **decoherence said:**
> it might break texlive, but if i'm right it should fix dpkg/apt.

rather than delete it, try something more temporary

```
chmod -x /usr/local/bin/install-info
```

that will keep it from running and ubuntu should move on to the next, proper install-info. if everything goes kablooey, you can reverse it with

```
chmod +x /usr/local/bin/install-info
```

let us know!

PS if they suggest running the installer as non-root then I would tend to assume (perhaps incorrectly) that they will add the location of whatever binaries they install to your path for you. if they don't then their instruction should explicitly tell you to add the location to the path.

if neither of these are the case, i'd report a usability bug to whomever maintains it.

WOW..that did it! I took of the execution permissions on /usr/local/install-info like you suggested and ran apt-get upgrade and it fixed all of it! The cool part is it did not break texlive. I compiled my article without any problems.

Thanks alot for your help!

---

### Post by decoherence on 2008-12-31
> **linuxnovice said:**
> WOW..that did it! I took of the execution permissions on /usr/local/install-info like you suggested and ran apt-get upgrade and it fixed all of it! The cool part is it did not break texlive. I compiled my article without any problems.

Thanks alot for your help!

whew! thanks, i really needed that. this evening just turned crappy for me. no, nothing to do with this or ubuntu! ;) but nice to see something go right :)

---

