---
title: "apt-get name resolution issues"
date: 2005-06-02
forum: Networking &amp; Wireless
---

### Post by Craig Prevallet on 2005-06-02
I have the following problem:
 
 penguin@Longhorn:~$ sudo apt-get install ace-of-penguins
 Reading package lists... Done
 Building dependency tree... Done
 The following NEW packages will be installed:
 ace-of-penguins
 0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
 Need to get 225kB of archives.
 After unpacking 561kB of additional disk space will be used.
 0% [Connecting to us.archive.ubuntu.com (1.0.0.0)]
 
 The connection never completes. The DNS number (1.0.0.0) looks wrong to me. 
 However the connection proceeds if I fire up a browser and type in the host name (us.archive.ubuntu.com). I'm on an ADSL internet connection and can ping just fine. Any ideas?

---

### Post by defkewl on 2005-06-02
Why not try other repo. I got the same message too from those repo. :)

---

