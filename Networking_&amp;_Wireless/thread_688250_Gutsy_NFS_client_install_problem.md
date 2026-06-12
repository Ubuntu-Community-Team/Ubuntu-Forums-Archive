---
title: "Gutsy NFS client install problem"
date: 2008-02-05
forum: Networking &amp; Wireless
---

### Post by srkirk on 2008-02-05
Hello,

When I try to install NFS client software on my Xubuntu Gutsy machine, I get the following error:
$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree
Reading state information... Done
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nfs-common (1:1.1.1~git-20070709-3ubuntu1) ...
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN0> line 1.
dpkg: error processing nfs-common (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 nfs-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

Does anyone know how to fix this? I don't need the server stuff ( I already have another NFS server on my network, I just want to be able to connect my Xubuntu machine as a client).

Many thanks in advance!

---

### Post by dmizer on 2008-02-05
you will also need to install portmap.  see this thread:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

it has directions for both client only install, as well as server install.

---

### Post by srkirk on 2008-02-05
> **dmizer said:**
> you will also need to install portmap.  see this thread:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

it has directions for both client only install, as well as server install.

Many thanks for the quick reply! Good links, but I tried this already. Portmap is already installed.

$ sudo apt-get install portmap nfs-common
[sudo] password for steve:
Reading package lists... Done
Building dependency tree
Reading state information... Done
portmap is already the newest version.
nfs-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up nfs-common (1:1.1.1~git-20070709-3ubuntu1) ...
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN0> line 1.
dpkg: error processing nfs-common (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 nfs-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

The problem is specifically that the nfs-common install seems to be breaking.

---

### Post by dmizer on 2008-02-05
it was only yesterday when i last installed nfs-common on a gutsy client.

try updating and upgrading first:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
then try reconfiguring nfs-common
```
sudo dpkg-reconfigure nfs-common
```
if that doesn't work, try reinstalling:
```
sudo aptitude reinstall nfs-common
```

---

### Post by srkirk on 2008-02-05
> **dmizer said:**
> it was only yesterday when i last installed nfs-common on a gutsy client.

try updating and upgrading first:
```
sudo aptitude update
sudo aptitude safe-upgrade
```
then try reconfiguring nfs-common
```
sudo dpkg-reconfigure nfs-common
```
if that doesn't work, try reinstalling:
```
sudo aptitude reinstall nfs-common
```

The 'update' command checked across Gutsy repositories, but did not install anything new.

The 'safe-upgrade' command saw that nfs-common had only been partially installed, tried to install it and failed with the same error as before.

Output from the third (dpkg-reconfigure) command was:

/usr/sbin/dpkg-reconfigure: nfs-common is broken or not fully installed

The final command ('reinstall') failed with the same error as before, tried to recover, then failed yet again with the same error message as before.

---

### Post by dmizer on 2008-02-06
please post the contents of your /etc/apt/sources.list

---

### Post by srkirk on 2008-02-06
> **dmizer said:**
> please post the contents of your /etc/apt/sources.list

OK, here goes ..

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
 
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy main restricted
 
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates universe
 
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
 
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by dmizer on 2008-02-06
go through your sources list and change them from sweeden (se) to the states (us) like so:

```

deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy universe
deb http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://[COLOR="Red"]us[/COLOR].archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://se.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```
update your sources:
```
sudo aptitude update
```
reinstall nfs-common
```
sudo aptitude reinstall nfs-common
```
see if that fixes things.  could just be that sweeden repo is corrupt.  i run into this on occasion with japan's repo.

---

### Post by srkirk on 2008-02-07
> **dmizer said:**
> go through your sources list and change them from sweeden (se) to the states (us) like so:

< repository list snipped >

update your sources:
```
sudo aptitude update
```
reinstall nfs-common
```
sudo aptitude reinstall nfs-common
```
see if that fixes things.  could just be that sweeden repo is corrupt.  i run into this on occasion with japan's repo.

OK, did this. Unfortunately, the result is the same as before (the error is still there, and it will not install on my PC).

The odd thing is that I have now installed exactly the same version of nfs-common in the Xubuntu distribution (eeeXubuntu RC3) on my Asus EEE, and it installs and works perfectly :confused:

Is there any way to make the install process more verbose, in a way that might indicate the cause of the installation error ?

---

### Post by torypatnoe on 2008-02-07
This may have just been a quirk, but I had the same problem and this fixed it:

sudo apt-get install util-linux
sudo aptitude reinstall  portmap
sudo aptitude reinstall  nfs-common

---

### Post by MichaleR on 2008-02-10
nfs mounting also broke on my system after the gutsy upgrade.

Installing nfs-common repaired the issue.

Prior to installing nfs-common the error would be:
root@berry:/etc# mount /music
mount: wrong fs type, bad option, bad superblock on eye:/var/music,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

(helpful, really narrows down the possibilities)

dmesg showed no output
starting logging for nfs on the server (eye in my case) showed no contact from the client (berry)

After installing nfs-common mounting of nfs file systems work.

---

### Post by srkirk on 2008-02-13
@torypatnoe: Thanks for your advice! I tried what you suggested, but still got the same error messages.

It appears that something of the nfs-common package gets installed, but not all.

Here's the error message I get when I attempt to mount a remote NFS server:

mount.nfs: rpc.statd is not running but is required for remote locking.
   Either use '-o nolocks' to keep locks local, or start statd.

I have tried manually starting rpc.statd using sudo but it doesn't seem to work.

Does this provide any more clues?

Thanks!

---

### Post by srkirk on 2008-02-14
OK, I think I've solved the problem, so for the benefit of anyone else who is interested, here it is:

I think the cause of the problem is the post-install configuration script that is run whenever the nfs-common package is installed.

After a failed installation, I executed this file  (/var/lib/dpkg/info/nfs-common.postinst) manually using sudo. The script shutdown, then restarted, the nfs utilities running on my machine.

After this, I was able to mount a remote NFS server with no problems at all! 

It still seems very odd that this script didn't execute properly first time during the install. I am still not 100% convinced that this is a perfect solution, but it's the best I can find so far. If anyone has any warnings to pass on that I might not be doing the right thing, or that I'm accidentally configuring my system in a dangerous way, please let me know ASAP. To everyone else, YMMV, but I hope this helps if you have similar problems.

---

### Post by lucaspr on 2008-03-10
> **srkirk said:**
> @torypatnoe: Thanks for your advice! I tried what you suggested, but still got the same error messages.

It appears that something of the nfs-common package gets installed, but not all.

Here's the error message I get when I attempt to mount a remote NFS server:

mount.nfs: rpc.statd is not running but is required for remote locking.
   Either use '-o nolocks' to keep locks local, or start statd.

I have tried manually starting rpc.statd using sudo but it doesn't seem to work.

Does this provide any more clues?

Thanks!

Same problem here..

Gat a Xubuntu LAMP server with NFS exports runnnig and wasn't able to connect my Ubuntu gutsy machine.. So I decided to switch to another debian distro : Dreamlinux..  Which is partially based on... Ubuntu. So the problem rises again.. Exactly the same error as above...:confused:

Could it be this bug?? 
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=433386](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=433386)

---

