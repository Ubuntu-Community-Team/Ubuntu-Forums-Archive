---
title: "How to build a cluter based on 2 Laptops"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by yuanfangcan on 2006-11-29
> I have two laptops with ubuntu system. I got NFS
> working also ssh 
> without password prompt between the two laptops. I
> also installed MPICH.
> And my simple parallel code is compiled
> successfully. But after I use 
> mpirun -np n xxx to submit my job. it doesn't work.
> 
> what could be the problem?
> 
> I guess the problem may be the NFS exports setting
> on my head node(one 
> of my laptop). Even though I can mount the shared
> folder to my internal 
> node. I don't have write permission from my internal
> node. But in my 
> exports I did set rw permission.  So I don't know
> what is wrong

---

### Post by omid on 2007-07-30
Have yor boot yor mpd?
modboot -np 2 

maybe [this]("https://wiki.ubuntu.com/MpichCluster") help you

---

