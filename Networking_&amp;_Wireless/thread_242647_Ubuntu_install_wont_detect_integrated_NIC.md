---
title: "Ubuntu install wont detect integrated NIC"
date: 2006-08-23
forum: Networking &amp; Wireless
---

### Post by Ankton on 2006-08-23
Hi, I am attempting to install ubuntu-6.06.1-server-i386 on an IBM e-server Xseries 300 and it will not detect the network card. I had a copy of Debian on the same machine and it detected the network card fine and worked nicely. 

I have tried putting other NICs in the pci slots but they arent detected either this is a freshly formatted system and im starting from scratch. Any ideas on how to proceed please??

---

### Post by packhamster on 2006-10-17
Check your BIOS version. I had the same problem and flashed it to version 120 (from 116). The installation will recognize the NICs, however now the system hangs during startup while "Loading hardware drivers..."

---

