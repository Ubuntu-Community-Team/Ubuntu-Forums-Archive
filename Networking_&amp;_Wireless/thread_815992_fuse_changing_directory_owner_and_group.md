---
title: "fuse changing directory owner and group"
date: 2008-06-02
forum: Networking &amp; Wireless
---

### Post by jamaas on 2008-06-02
Relative noob here ... 

Attempting to set up Tomboy notes to sync to a ssh server using fuse as it requires.  When I first install tomboy it creates a directory ~/.tomboy that contains /sync-sshfs
when I install the ssh addin, and at first it has owner and group as the correct username to go with ~.  However when I try to setup the sync parameters and connect it the first time the .tomboy.log file says it could not connect to the test file and when I check this /sync-sshfs subdirectory, the owner and group have changed to numbers that I didn't set.  Sudo rm will not remove this directory and when I change the terminal to su using sudo su all the file permissions turn into ????   .... can someone point me in the right direction, is this a bug or something I'm doing wrong.

Thanks a bunch as usual

Jim

---

