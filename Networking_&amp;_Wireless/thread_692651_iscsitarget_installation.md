---
title: "iscsitarget installation"
date: 2008-02-10
forum: Networking &amp; Wireless
---

### Post by Einewton on 2008-02-10
Version: Ubuntu 7.10

I received an error when installing iscsitarget, and I didn't write it down because I thought I could just un-install it.

When I went to uninstall it I get:
**E: iscsitarget: subprocess pre-removal script returned error exit status 1**

Here is a more detailed message when I try to use apt-get to remove:

```

einewton@Einewton:~/iSCSI/iscsitarget-0.4.15$ sudo apt-get -f remove --purge open-iscsi
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  iscsitarget: Depends: iscsitarget-module but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Here is my Kernel Version.
einewton@Einewton:~/iSCSI/iscsitarget-0.4.15$ cat /proc/version
Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Fri Feb 1 04:59:50 UTC 2008


I really would like to setup iSCSITarget on my box, but everything seems to be blowing up now.

The real kicker is now, I can't install anything. Here's an example:
```

einewton@Einewton:~/iSCSI/iscsitarget-0.4.15$ sudo apt-get install python
Reading package lists... Done
Building dependency tree
Reading state information... Done
python is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  iscsitarget: Depends: iscsitarget-module but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```


Now, I really need help!  :(

---

### Post by jan quark on 2008-02-11
try running this and post any error messages please

```

sudo apt-get -f install
```


thank you

---

### Post by hoangminh88 on 2008-02-19
when I 'make'. Terminal show:
```
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/root/iscsitarget-0.4.15/kernel modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /root/iscsitarget-0.4.15/kernel/event.o
/root/iscsitarget-0.4.15/kernel/event.c: In function &#8216;event_init&#8217;:
/root/iscsitarget-0.4.15/kernel/event.c:98: warning: passing argument 4 of &#8216;netlink_kernel_create&#8217; from incompatible pointer type
/root/iscsitarget-0.4.15/kernel/event.c:98: error: too few arguments to function &#8216;netlink_kernel_create&#8217;
make[2]: *** [/root/iscsitarget-0.4.15/kernel/event.o] Error 1
make[1]: *** [_module_/root/iscsitarget-0.4.15/kernel] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [kernel] Error 2
```

Plz help me to fix it.

---

### Post by Einewton on 2008-02-26
> **jan quark said:**
> try running this and post any error messages please

```

sudo apt-get -f install
```


thank you

This did NOT work...

What i ended up doing is finding every file/folder related to iscsitarget, and deleting it (rm-rf) then i had to update my aptget, and my apt-get started to work again...


Still couldn't get iscsitarget to work, i suppose i'll just support iscsitarget on windows since it's not very mature for Linux.

---

### Post by _ufo_ on 2008-03-16
I tried a simple patch of iscsitarget-0.4.15/kernel/event.c line 98. 

Change from:
nl = netlink_kernel_create(NETLINK_IET, 1, event_recv, THIS_MODULE);

To:
nl = netlink_kernel_create(NETLINK_IET, 1, event_recv, 0, THIS_MODULE);

I seems to work (created/mounted/used a target without failure).
Unfortunately I don't if the extra argument (struct mutex*) is needed.

My investigations tells it is introduced in kernel 2.6.21 or 2.6.22.

Tests where performed on:
Ubuntu-7.10 and kernel 2.6.22-14-server

---

