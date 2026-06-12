---
title: "Ubuntu installation on netbook"
date: 2009-12-19
forum: New to Ubuntu
---

### Post by Bob Appleby on 2009-12-19
After more than a decade I should be getting broadband just before New Years eve, so I’m back to working on ubuntu after the frustration of trying to do a phone modem hookup last spring.

Background on my computer: HP mini 1115NR with no hard drive. 8 Gig C drive. 8 Gig D drive in the  form of a PNY optima SDHC.
 
I downloaded a copy of 9.10 and installed it within windows on the D drive to prevent using too much of the C drive. Spent several hours learning how to use it. Everything went smoothly. Then I went out and bought a 16 gig SanDisk SDHC and replaced the 8 Gig card. The installation of 9.10 on the new card seemed to go well until I restarted the computer and asked for ubuntu. The computer displayed grub:

I tried typing boot and was informed that there was no kernel. Reinstallation in safe mode yielded the same problem. Reinstallation on drive C was normal. Retried D and got grub: again.

Help!!

Bob

---

### Post by spiderbatdad on 2009-12-19
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
Not trying to just pawn a load of reading off on you, but not too clear on what your set up is. It sounds like you are running 2 disks? In that case grub is on the previous and needs to be pointed to the filesystem...the guide will tell you how to do this. Or a complete installation on a new drive produces the grub prompt? This is also addressed.

---

