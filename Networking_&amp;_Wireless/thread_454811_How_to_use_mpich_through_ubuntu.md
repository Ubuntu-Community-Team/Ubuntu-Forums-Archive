---
title: "How to use mpich through ubuntu"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by Mayank Sharma on 2007-05-25
Hi!
          I want to  go for parallel programming using mpich. I have seen mpich package in ubuntu. I have one ubuntu box(master) and other is fedora core 6 box(slave). Is their any pre setting before installing mpich. Is it nessary to have mpich install on both master and slave or only on master.

---

### Post by omid on 2007-07-30
I've made a wiki for MPICH/Clustring , hope it will be useful for you.

[https://wiki.ubuntu.com/MpichCluster]("https://wiki.ubuntu.com/MpichCluster")

---

### Post by m_atif on 2007-09-22
Thanks... Great tutorial for beginners. 
One small issue though, in the final testing and staring of mpd's

After all run mpd daemon:
mpiu@ub0:~$ mpdboot *-np 4

-np 4 does not work... should'nt it be --totalnum=4?

---

