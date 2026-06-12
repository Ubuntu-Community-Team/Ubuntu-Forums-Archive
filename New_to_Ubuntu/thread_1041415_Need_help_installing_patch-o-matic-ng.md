---
title: "Need help installing patch-o-matic-ng"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by looi76 on 2009-01-16
Hi, I have been having problems installing **patch-o-matic-ng-20081130**. For installing patch-o-matic-ng I need to run the runme file in the terminal. When I run it, it asks me for the kernel source directory?  /usr/src/linux-headers-2.6.27-9 which is ok! then it asks me for Where is your iptables source code directory? [/usr/src/iptables]. I don't know where the source code directory for iptables is. I have installed iptables through Synaptic Package Manager.

---

### Post by compiledkernel on 2009-01-16
sudo aptitude install iptables-dev netfilter-extensions-source , I think should do it.

---

### Post by looi76 on 2009-01-16
I still don't know the iptables directory!

[IMG]http://img187.imageshack.us/img187/4651/screenshotko7.png[/IMG]

---

### Post by starling on 2009-01-29
Arg! I'm having the same trouble. I tried the latest iptables source from the netfilter website (1.4.2), and patch-o-matic-ng-20040302 from the same. I then ./runme and it says the folder "doesn't look like like and iptables source tree". Also tried it with the iptables source from the repo with same result.

iptables folder looks like this:

```
root@server:/usr/src# ls iptables/
aclocal.m4    INCOMPATIBILITIES       iptables.8.in          iptables-xml.c
autogen.sh    INSTALL                 iptables-apply         iptables.xslt
compile       install-sh              iptables-apply.8       libipq
config.guess  ip6tables.8.in          iptables.c             libiptc
config.h.in   ip6tables.c             iptables-multi.c       ltmain.sh
config.sub    ip6tables-multi.c       iptables-multi.h       Makefile.am
configure     ip6tables-multi.h       iptables-restore.8     Makefile.in
configure.ac  ip6tables-restore.8     iptables-restore.c     missing
COPYING       ip6tables-restore.c     iptables-save.8        release.sh
depcomp       ip6tables-save.8        iptables-save.c        xtables.c
extensions    ip6tables-save.c        iptables-standalone.c  xtables.pc.in
include       ip6tables-standalone.c  iptables-xml.8
```

Perhaps this is an incompatible version of iptables? What version should I have?

---

### Post by eee1000huser on 2009-02-18
Has anyone had any luck compiling patch-o-matic-ng on Ubuntu 8.10?

Also, is does this solve the multiple VPN (pptp) problem behind NATed boxes?


Cheers,

-e

---

### Post by Dimaxwell on 2009-08-02
> **starling said:**
> Arg! I'm having the same trouble. I tried the latest iptables source from the netfilter website (1.4.2), and patch-o-matic-ng-20040302 from the same. I then ./runme and it says the folder "doesn't look like like and iptables source tree". Also tried it with the iptables source from the repo with same result.

iptables folder looks like this:

```
root@server:/usr/src# ls iptables/
aclocal.m4    INCOMPATIBILITIES       iptables.8.in          iptables-xml.c
autogen.sh    INSTALL                 iptables-apply         iptables.xslt
compile       install-sh              iptables-apply.8       libipq
config.guess  ip6tables.8.in          iptables.c             libiptc
config.h.in   ip6tables.c             iptables-multi.c       ltmain.sh
config.sub    ip6tables-multi.c       iptables-multi.h       Makefile.am
configure     ip6tables-multi.h       iptables-restore.8     Makefile.in
configure.ac  ip6tables-restore.8     iptables-restore.c     missing
COPYING       ip6tables-restore.c     iptables-save.8        release.sh
depcomp       ip6tables-save.8        iptables-save.c        xtables.c
extensions    ip6tables-save.c        iptables-standalone.c  xtables.pc.in
include       ip6tables-standalone.c  iptables-xml.8
```

Perhaps this is an incompatible version of iptables? What version should I have?

#/usr/src/iptables/configure

After that run ./runme

[http://www.debian-administration.org/articles/518](http://www.debian-administration.org/articles/518)

---

### Post by bodhi.zazen on 2010-06-08
This is a very old thread, but it comes up on a google. search so I shall answer ...

First, it helps if you have a few dependencies already installed

```
sudo apt-get install dpkg-dev
```You download the Ubuntu iptables source code with 

```
sudo apt-get source linux-image-`uname -r`
sudo apt-get source iptables
```You then cd into the iptables source directory ( iptables-1.4.4 at the time of this post ) and run ./configure

```
cd iptables-1.4.4
./configure
```Once the ./configure is finished, patch-o-matic-ng will recognize the directory.

You may set it either via export

```
export KERNEL_DIR=/full/path_to/kernel_source_code
export IPTABLES_DIR=/full/path_to/iptables-1.4.4
./runme
``` or when you run patch-o-matic-ng

Last you would recompile your kernel (netfilter) AND iptables (they are separate) and install them.

Do not forget to build an initrd and update grub

Reboot to the new kernel. 

Note: patch-o-matic is, IMO, poorly documented. Are you **sure** you need to use it , some of the features have been added and there is less a need to patch.

In addition, by default, only one patch (patchlet) was in the most recent snapshot, one would need to track down and add additional patches if needed ...

---

