---
title: "resize ubuntu"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by gkraju on 2009-02-24
i have only 200 mb in my ubuntu 
i have 10GB free from another drive 
i used Gparted and seperated 10 gb from the drive 
now i want to add that 10 gb to present ubuntu file system 
how to do please help
help thanks in advance

---

### Post by carml on 2009-02-24
Have you got GPartred Live?If you don't then dowload the ISO,burn it to disk,insert into your cd/dvd reader and reboot.

---

### Post by gkraju on 2009-02-24
> **carml said:**
> With which software did you obtain that 10 gb of space?
Gparted

---

### Post by carml on 2009-02-24
Sorry I missed before and correct just a while ago. Can you please read again my first post?

---

### Post by kahlil88 on 2009-02-24
I don't think you can allocate space from a separate hard drive to a partition. If you have a swap partition on the drive Ubuntu is installed on, you an remove it and expand the Ubuntu partition a bit, then use the other drive for swap.

---

### Post by gkraju on 2009-02-24
> **kahlil88 said:**
> I don't think you can allocate space from a separate hard drive to a partition. If you have a swap partition on the drive Ubuntu is installed on, you an remove it and expand the Ubuntu partition a bit, then use the other drive for swap.

i cant understand what are you saying
can you explain it briefly ?

---

### Post by carml on 2009-02-24
@ kahlil88 
Maybe you're right,if so I'm sleping and apparently awake :lolflag:.
I supposed it was the same hard drive :).

---

### Post by carml on 2009-02-24
> **gkraju said:**
> i cant understand what are you saying
can you explain it briefly ?
He's suggesting to reduce the swap partition,you can do so only booting with a Gpaterd live disk,because the partition must be not in use.
Hope this clearify the other post.:)

---

### Post by gkraju on 2009-02-24
> **carml said:**
> @ kahlil88 
Maybe you're right,if so I'm sleping and apparently awake :lolflag:.
I supposed it was the same hard drive :).

i have 5 GB in the same drive too
tell me how to allocate it to ubuntu file system using gparted or any other software 
pls help i have only 200 mb

---

### Post by carml on 2009-02-24
Ok man: 
1. Take the disk with your version of Gparted Live (if haven't you any downolad the iso and burn to disk at low speed);
2. Take a note on a sheet of the order of the partition on the drive,the one you want to modify.
You'll note something like sda1,sda2 etc,this info can be reached by System->Administration_Partition Editor if you already have Gparted installed under Ubuntu.
If you haven't Gparted installed go to Applications->Accessories-Terminal and type " sudo fdisk -lu " without brackets.
3. Insert the Gparted's disk onto your cd/dvd drive and reboot.
When you boot choose Safe mode or something similar to set Gparted's preferences and then you can move your partitions. :p

---

### Post by kahlil88 on 2009-02-24
I usually just run GParted from the Ubuntu Live CD.

---

### Post by carml on 2009-02-24
I used an Alternate disk and I prefer Gparted,everyone has his predilections. :p

---

### Post by Elfy on 2009-02-24
It might help to post the results of so that we can see exactly how your drives are laid out at present.

```
sudo fdisk -l
```

If you created a default ubuntu install then you might well find that your install is inside an extended partition.

If that is the case then you will need to expand that prior to resizing the ubuntu partition. I'm not sure whether you can use the ubuntu install livecd to resize from either end of a partition - it might indeed be necessary to use a prtition editor livecd such as gparted.

---

### Post by gkraju on 2009-02-24
> **carml said:**
> Ok man: 
1. Take the disk with your version of Gparted Live (if haven't you any downolad the iso and burn to disk at low speed);
2. Take a note on a sheet of the order of the partition on the drive,the one you want to modify.
You'll note something like sda1,sda2 etc,this info can be reached by System->Administration_Partition Editor if you already have Gparted installed under Ubuntu.
If you haven't Gparted installed go to Applications->Accessories-Terminal and type " sudo fdisk -lu " without brackets.
3. Insert the Gparted's disk onto your cd/dvd drive and reboot.
When you boot choose Safe mode or something similar to set Gparted's preferences and then you can move your partitions. :p


 i did what you said i freed 3GB but it is not included in the file system
instead it is mounted along with the other hard drive
ie. it is now in the /media folder 



[IMG]/home/rajkumar/Desktop/start.png[/IMG]

---

### Post by carml on 2009-02-24
You have to move that space under the partition where lies Ubuntu.

---

### Post by Elfy on 2009-02-24
It certainly sounds as though it is on a seperate hdd - but without any concrete data it's all a bit of a guess ...

If it is on a seperate hdd then you will not be able to add it to the ubuntu install - you will though be able to add it so that it mounts on boot and it will be useable space.

---

