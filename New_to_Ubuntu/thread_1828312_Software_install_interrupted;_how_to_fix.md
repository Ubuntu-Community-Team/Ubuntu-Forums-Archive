---
title: "Software install interrupted; how to fix?"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by flyingsolo on 2011-08-18
I was installing dvd::rip from synaptic manager in Hardy Heron (using old version b/c old computer graphics not supported beyond HH) but computer hung up/froze. Required restart but didn't complete install. If I try to reinstall with sudo apt-get install dvd::rip, I get:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

and then if I run the command above, I get:

dpkg: parse error, in file '/var/lib/dpkg/updates/0000' near line 5 package 'dvdrip-doc':
 EOF before value of field `Maintainer' (missing final newline)

Any suggestions how to proceed? Many thanks.

---

### Post by jramshu on 2011-08-18
Try these:
```
sudo dpkg --clear-avail
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by flyingsolo on 2011-08-18
Thanks but I get:

michael@mvtd ubuntu:~$ sudo dpkg --clear-avail
sudo: unable to resolve host mvtd ubuntu

Still stumped!

---

### Post by jramshu on 2011-08-19
Seems as something has changed in the hosts file.

```
cat /etc/hosts
```

Make sure "mtvd ubuntu' is still there and hasn't been changed.

---

### Post by flyingsolo on 2011-08-19
Still seems to be there:

michael@mvtd ubuntu:~$ cat /etc/hosts
127.0.0.1	localhost.localdomain	localhost
127.0.1.1	mvtd ubuntu
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by flyingsolo on 2011-08-22
*Bump*
Hoping for some extra insight to the original issue in 1st post above; how to deal with the dpkg: parse error message. My naive reading of the message is that I'm supposed to edit line 5 in the file at /var/lib/dpkg/updates/0000
but to what? Do I just delete line 5? Line 5 of that file is:
Installed-Size:  1488
I wouldn't have a clue what I should change that to or even if I should.
(I probably know just enough about this to be dangerous!)

---

