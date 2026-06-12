---
title: "Slow network transfer speed. Need help please!"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Predtech on 2008-09-16
Hi guys. I recently rebuilt my old pc as a small form factor server but the strange thing i find is that transferring files between both pc's (both running ubuntu 8.04) i only get about 4.3MB/s which is deathly slow, that's only about 40Mb/s i think. I have 100Mb/s on the slowest and 1000Mb/s on my main pc so why am i getting such slow transfer rates??

I am running a brand new Dlink DIR-615 with the latest firmware as my router.

Thanks

---

### Post by mrsteveman1 on 2008-09-16
It's actually around 4.3x8 = 34.2mbps which is a bit slow for 100mbps ethernet.

You are using samba right? Have you tried any other protocols?

---

### Post by Predtech on 2008-09-16
this whole server thing is basically a new concept to me. I have never had the need to run more than 1 pc at a time until now. What other options do i have besides smb???

---

### Post by mrsteveman1 on 2008-09-16
Offhand i can't think of a good way to benchmark the local network without using one of the common file sharing protocols, perhaps someone else can chime in with a good way to see what the bottleneck is if it isn't samba. Is the CPU spiked while you are transferring stuff?

Samba isn't usually that slow though, esp if you have 100mbps to play with. 

There are a couple of other network protocols for file sharing, but nothing as easy as samba to setup and use. NFS is one a lot of people use, there are tutorials on how to set that up if it isn't already in the sharing dialog (can't look right now). There is also SSHFS, which isn't hard to use but might actually be slower because its encrypted.

What are the hardware specs on this machine? I wouldn't think it would be working too hard just transferring stuff with samba but you never know.

---

### Post by figmentx on 2008-09-16
I would try swapping out a new ethernet cable first.  Also try to keep them away from power cables as much as possible.

---

