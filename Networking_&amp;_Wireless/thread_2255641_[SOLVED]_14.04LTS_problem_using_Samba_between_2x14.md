---
title: "[SOLVED] 14.04LTS problem using Samba between 2x14.04 machines"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by nyker on 2014-12-06
Im new to Ubuntu. I set up Samba on 2 14.04machines in LAN setup by using share option on a dir, did this on both machines, which resulted in samba been installed in the process.

both has static IP to facilitate portforwarding. I am able to connect Samba via smb://machine-name.local/share
using connect to server on BOTH machines. but when i click on browse network, i see the other machine but
not able to connect: get an unable to access location error.

please help. ty!

both on Ubuntu 14.04 64bit desktop OS.

---

### Post by SuperFreak on 2014-12-06
Could be permissions issue. You may have to grant Read (&Write) privileges for those directories. To do this open Samba in GUI and check that each directory in question has Read/write privileges. Then double click on directory and make sure that under Access tab you have granted permission to appropriate user

---

### Post by nyker on 2014-12-06
thanks for post, just checked, seems both sides the share directory has full privilages for everyone:
doing an ls -l on both shared dirs on each machine:

drwxrwxrwx 2 bbb bbb 4096 Dec  6 12:05 share

---

### Post by nyker on 2014-12-06
ok solved. apparently need to add a line in /etc/hosts for other LAN machines's name.

like:
155.165.175.10 other-machine-name 

samba was able to operate fine after that.

---

### Post by mörgæs on 2014-12-06
Please use Thread Tools for marking a thread solved.

---

