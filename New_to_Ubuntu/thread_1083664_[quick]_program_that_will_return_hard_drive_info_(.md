---
title: "[quick] program that will return hard drive info (RPM, cache, etc)?"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by earthpigg on 2009-03-01
Anyone know a program that will tell you basic data about a hard drive (internal and external)?

Ideally, it would detect all drives, and list the RPM's, and total cache, connection type (SATA, eSATA), etc.?


I've seen programs like this that will tell you activity and data about other components (RAM, CPU, etc.) but i'd like one for hard drives.

simple GUI app is preferred, but im not afraid to read a man file or use a live cd.

---

### Post by ikisham on 2009-03-01
Install lshw if you don't have it already. Then just type ```
sudo lshw
``` and it will output all hardware in the pc. Then just google for the drives you have to find more on their specs.

---

