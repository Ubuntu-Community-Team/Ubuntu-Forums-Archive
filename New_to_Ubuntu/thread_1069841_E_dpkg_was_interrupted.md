---
title: "E: dpkg was interrupted"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by Farzid.Klipaw on 2009-02-14
Hi, I am having this problem whenever I try to run apt-get. I have done a search and see that this is a common problem but none of the solutions work for me.

The full error message when I try something like apt-get install:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


I type "sudo dpkg --configure -a" like it says, then I get:

dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
Aborted

I then try "sudo apt-get update && sudo apt-get upgrade" and it scrolls through a bunch of stuff then

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY[...] 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.


Then I try apt-get install again with something and it seems to work, but then it crashes at the end:

Setting up vpnc (0.5.1r275-1ubuntu1) ...
dpkg: ../../src/packages.c:221: process_queue: Assertion `dependtry <= 4' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly


And the following crash notice appears in the system tray:

Sorry, the package "libxine1-bin 1.1.15-0ubuntu3.1" failed to install or uprgade.

Any help would be great!

and P.S. I am running 8.10


EDIT: it appears there is a new update for dpkg but I can't even install it because of this problem!

I get the error:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by wolfen69 on 2009-02-14
to fix the medibuntu signature problem: 
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

then
```
sudo apt-get install -f
```

post back after that.

---

### Post by gettinoriginal on 2009-02-14
cache open error indicates that you have more than one package manager open at the same time.  You may only have one (Synaptic OR Terminal OR Add/Remove) open at a time.

---

### Post by wolfen69 on 2009-02-14
also, did you enable all the repos in system>administration>software sources?

---

