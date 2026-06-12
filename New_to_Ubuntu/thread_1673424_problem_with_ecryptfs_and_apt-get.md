---
title: "problem with ecryptfs and apt-get"
date: 2011-01-22
forum: New to Ubuntu
---

### Post by eflix on 2011-01-22
Hello!, I'm having a problem with the package system. If I try to install some package, I get this error:
```
root@ubuntu:/home/lautaro# apt-get install audacious
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 audacious : Depends: audacious-plugins (>= 2.4.2) but it is not going to be installed
             Depends: libaudclient2 (= 2.4.2-1) but it is not going to be installed
             Depends: libaudcore1 (= 2.4.2-1) but it is not going to be installed
             Depends: libmcs1 but it is not going to be installed
             Depends: libmowgli2 (>= 0.7.0) but it is not going to be installed
 ecryptfs-utils : Depends: libecryptfs0 (>= 77) but it is not going to be installed
                  Depends: keyutils but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```
Next, I do as the prompt says, I "apt-get -f install" and this is the output:
```
root@ubuntu:/home/lautaro# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libecryptfs0 ecryptfs-utils keyutils
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  keyutils libecryptfs0
The following NEW packages will be installed:
  keyutils libecryptfs0
0 upgraded, 2 newly installed, 0 to remove and 472 not upgraded.
Need to get 0 B/90.6 kB of archives.
After this operation, 377 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package keyutils.
(Reading database ... 137659 files and directories currently installed.)
Unpacking keyutils (from .../keyutils_1.4-1_i386.deb) ...
Selecting previously deselected package libecryptfs0.
Unpacking libecryptfs0 (from .../libecryptfs0_84-0ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up keyutils (1.4-1) ...
Setting up libecryptfs0 (84-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```
So far, so good. I can't get to install and try new stuff, but the problem is when I reboot and I can't read my home partition. The only solution gets me right at the beginning, doing an "apt-get autoremove" which uninstalls the aforementioned packages.
```
root@ubuntu:/home/lautaro# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ecryptfs-utils keyutils libecryptfs0
0 upgraded, 0 newly installed, 3 to remove and 472 not upgraded.
After this operation, 893 kB disk space will be freed.
Do you want to continue [Y/n]?
```
How do I get out of this vicious packaging circle? 
Thanks! (Currently using lubuntu 10.10)

---

### Post by eflix on 2011-01-22
> **eflix said:**
> 
So far, so good. I can't get to install and try new stuff,
 
Correction: In this line I meant I'm able to install programs through apt-get.

---

### Post by gmargo on 2011-01-22
> **eflix said:**
> 
0 upgraded, 2 newly installed, 0 to remove and [COLOR=Red]472 not upgraded[/COLOR].


The solution should be obvious.  Upgrade first.

---

### Post by eflix on 2011-01-22
I found the solution [in this post]("http://ubuntuforums.org/showthread.php?t=1373904&highlight=libecryptfs0"), I followed instructions from there except for 'rm -rf $PRIVATE', which happens to be your personal directory.
I quote a line from that post: > I would say step 5 is a bit wrong : there's no need to delete $PRIVATE, which was for me my home....


---

### Post by eflix on 2011-01-22
> The solution should be obvious. Upgrade first.
Yeah, I'm updating ubuntu right now, but I wanted to sort out this encription problem first. Thanks!

---

