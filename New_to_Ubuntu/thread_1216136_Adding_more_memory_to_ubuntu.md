---
title: "Adding more memory to ubuntu"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by frogchris on 2009-07-17
I'm dual booting window vista and ubuntu. I been using ubuntu even more now ,but when I installed it I only used 18 GB of free space. Does anyone know how I could add more memory for do i just have to reinstall ubuntu?

---

### Post by Bucky Ball on 2009-07-17
Memory is RAM, you are talking hard drive space I think.

Boot from the live CD and start partition manager (gparted) in there. Now you can resize your partitions. 

I strongly advise you to backup anything you don't want to loose (personal data) before doing this, just in case something goes wrong (not likely but better to be safe than sorry). If you are expanding a partition, you need to make sure you are expanding it into consecutive free space (ie if the free space is at the end of the disk and there is another partition between it and the one you want to expand, you are going to need to do some manual data swapping and thinking.

Good luck.

:)

---

### Post by RomeReactor on 2009-07-17
Hi. I'm not sure what you want to do... do you want to expand your Ubuntu partition, or add more RAM to the system?

EDIT: Adding to what Bucky Ball said, if you only have Ubuntu and Vista in the hard drive (assuming they're on the same HD) you should defrag Windows at least a couple of times before resizing the Ubuntu partition because it will also resize the Vista partition, making it smaller. And remember to always back up your data.

---

### Post by raymondh on 2009-07-17
> **frogchris said:**
> I'm dual booting window vista and ubuntu. I been using ubuntu even more now ,but when I installed it I only used 18 GB of free space. Does anyone know how I could add more memory for do i just have to reinstall ubuntu?

Hello and welcome !

Firstly, is this a WUBI install (ubuntu inside windows) or an independent, dual-boot (each OS in their own partition or referred to as side-by-side)?

If independent, and to access a terminal, go to applications > accessories. Kindly type and post back terminal outputs (one at a time)

```
sudo fdisk -l
```

That's a small L, not 1 nor i.

When required, would you know how to access gparted (system >administration > partition editor) from either the liveCD or your Ubuntu installation?

Lastly, are you also familiar with Vista's disk management tool.

Some early tips :

Back up your files and start defragging Vista :)

---

### Post by Bucky Ball on 2009-07-17
> **raymondhenson said:**
> Hello and welcome !

Firstly, is this a WUBI install (ubuntu inside windows) or an independent, dual-boot (each OS in their own partition)?

If independent, and to access a terminal, go to applications > accessories. Kindly type and post back terminal outputs (one at a time)

```
sudo fdisk -l
```That's a small L, not 1 nor i.

When required, would you know how to access gparted (system >administration > partition editor) from either the liveCD or your Ubuntu installation?

Lastly, are you also familiar with Vista's disk management tool.

Some early tips:

Back up your files and start defragging Vista :)

Interesting information but why all the questions? Some instructions and OP will soon let you know what they don't understand. 

One very important thing to remember is that the partition has to be UNMOUNTED to work on (resize etc). If OP wants to resize Ubuntu partition, this means LIVE CD, *NOT* from within running hard drive Ubuntu desktop (where the disk is of course mounted to run the OS).

---

