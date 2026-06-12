---
title: "Hardware drivers"
date: 2011-05-17
forum: New to Ubuntu
---

### Post by jocika011 on 2011-05-17
Dear Friends,

Yesterday I was trying to go to Administration > Hardware drivers and I got the message:

**Downloading package indexes failed please check your network status. Most drivers will not be available.**

I did activated drivers long time ago and my graphic running normally. I have 3D effects I can run HD Movies without the problem.

What should be the cause of this disturbing message?


[I]Ubuntu 10.04
INTEL Quad Core I7-930 2.8GHz 
DDR3 6GB [3x2GB] DDR1333 (PC3-10666) 
GIGABYTE GA-X58A-UD3R ( Intel X58/ICH10R - Socket 1366 - QPI 6400 MT/s ) 
ASUS ENGT240/DI/1GD3/A GeForce GT 240 1GB
SATA300 1.0To (1000GB) - 7200 WESTERN Caviar Black[/I]

---

### Post by wildmanne39 on 2011-05-17
> **jocika011 said:**
> Dear Friends,

Yesterday I was trying to go to Administration > Hardware drivers and I got the message:

**Downloading package indexes failed please check your network status. Most drivers will not be available.**

I did activated drivers long time ago and my graphic running normally. I have 3D effects I can run HD Movies without the problem.

What should be the cause of this disturbing message?


[I]Ubuntu 10.04
INTEL Quad Core I7-930 2.8GHz 
DDR3 6GB [3x2GB] DDR1333 (PC3-10666) 
GIGABYTE GA-X58A-UD3R ( Intel X58/ICH10R - Socket 1366 - QPI 6400 MT/s ) 
ASUS ENGT240/DI/1GD3/A GeForce GT 240 1GB
SATA300 1.0To (1000GB) - 7200 WESTERN Caviar Black[/I]

Hi, according to the message it could not connect to the server, possibly your where not connected to the internet at the time or there was a problem on there end.

---

### Post by jocika011 on 2011-05-17
> **wildmanne39 said:**
> Hi, according to the message it could not connect to the server, possibly your where not connected to the internet at the time or there was a problem on there end.

Thank you wildmanne39. Internet connection is OK and very stable. What scares me that this message pop up almost instantly. 

I have impression that is looking for the drivers in the wrong location. ???

---

### Post by NCLI on 2011-05-17
> **jocika011 said:**
> Thank you wildmanne39. Internet connection is OK and very stable. What scares me that this message pop up almost instantly. 

I have impression that is looking for the drivers in the wrong location. ???

It is not a scary problem, it's just a networking issue. Try running "sudo apt-get update" in a terminal, then post the output here.

---

### Post by wildmanne39 on 2011-05-17
> **jocika011 said:**
> Thank you wildmanne39. Internet connection is OK and very stable. What scares me that this message pop up almost instantly. 

I have impression that is looking for the drivers in the wrong location. ???

Hi, no, your drivers are already installed, you just clicked on to check for them again and it could not because it could not connect to the server.

---

### Post by jocika011 on 2011-05-17
> **wildmanne39 said:**
> Hi, no, your drivers are already installed, you just clicked on to check for them again and it could not because it could not connect to the server.

Dear All,


Thank you so much, 

I will try again tonight when I come home, and post the result here!

---

### Post by mastablasta on 2011-05-17
sometimes servers are down or busy and you get this message. simple solution is to switch to another repository server. There are plenty out there. Ubuntu usualyl ddefault to the closest/fastest one which is usually the one in your country. 
but there are others. sometimes i had to switch to neighbouring country server and got access there, but usually the local one is just fine.

---

### Post by jocika011 on 2011-05-17
> **mastablasta said:**
> sometimes servers are down or busy and you get this message. simple solution is to switch to another repository server. There are plenty out there. Ubuntu usualyl ddefault to the closest/fastest one which is usually the one in your country. 
but there are others. sometimes i had to switch to neighbouring country server and got access there, but usually the local one is just fine.

yessss

Thank you so much

---

