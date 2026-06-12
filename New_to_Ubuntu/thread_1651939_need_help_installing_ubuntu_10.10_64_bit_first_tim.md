---
title: "need help installing ubuntu 10.10 64 bit first time Linux user"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by Olyptic on 2010-12-23
So far i formatted HD2 like below and i have been looking through the forums and the help documentation but i dont know where to start. I dont know Linux commands so if i need to use them i can use a tutorial link. 

( HD1 ) SATA 320 GB Hard Drive /dev/sda

|---------40-GB---------|----------------280-GB--------------| 
| NTFS Windows 7 64 bit | app setups and installs and backup | 
 
 
 
( HD2 ) IDE ATA 232 GB Hard Drive /dev/sdb 
 
|---------------132-GB------------------|----4-GB---|--1-GB--|---20-GB---|---20-GB---|---blank---| 
| NTFS shared media and linux downloads |----Swap---|--/boot-|-----/-----|---/home---|---blank---| 
 
 
 
| = partition 
 
 
 
3.4 GHz Quad Core AMD CPU 
NVIDIA GeForce GT 220 1GB 
4 GB RAM

---

### Post by Foxheadz on 2010-12-24
[https://help.ubuntu.com/8.04/switching/installing.html](https://help.ubuntu.com/8.04/switching/installing.html) heres a complete guide to installing ubuntu. and I would suggest instead of having a /boot / and /home partition just make one big partition and mount it as / also you only really need like a 1g swap partition

---

### Post by Olyptic on 2010-12-24
ok thanks ill try that

---

### Post by Olyptic on 2010-12-24
ok i installed it i just didnt see a third selection box for / thats why i missed it earlier

---

