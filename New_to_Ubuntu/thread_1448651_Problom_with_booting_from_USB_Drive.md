---
title: "Problom with booting from USB Drive"
date: 2010-04-06
forum: New to Ubuntu
---

### Post by Running_Dualboot on 2010-04-06
Whenever i try yo boot from a FAT32 Formatted drive it boots correctly and then it comes up with an error msg that says "...Failed,  attempt to kill the 'something'


Ubuntu 8.04

---

### Post by mlentink on 2010-04-07
Are you trying to boot ubuntu off of a FAT32 drive? My first guess is that this will give you loads of permission problems, as FAT32 obviously does not support the linux permissions-scheme. I advise to reinstall formatting the drive as EXT3/4. I run a couple of test-environments that way without problems.

---

