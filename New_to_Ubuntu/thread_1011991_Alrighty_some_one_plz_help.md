---
title: "Alrighty some one plz help"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by mysticanonymous on 2008-12-15
I am trying to install kubuntu on my pc, and well it wants to partition my hard drive an theres nothing on my hard drive! and well it wont let me, it tells me it has failed continue through partition menu.. ? well can anyone tell me why? or how to fix it. i can run from the disc just fine, it lets me log into the pc with boot from disc, but i cant install it.

---

### Post by Michael.Godawski on 2008-12-15
hi mysticanonymous, 

can you give us your specs? Like ram, cpu, graphic card?

---

### Post by nhasian on 2008-12-15
if you can boot off the liveCD just fine you can partition your drive from there.  Then you can tell ubuntu to use the existing partitions during installation.

In Kubuntu go to 
*Start->Applications->System->Partition Editor*

or from the terminal you can just type

```
sudo gparted
```

You'll need one EXT3 parition for the root / filesystem, and another partition for SWAP.  Make the swap partition at least as large as your ram.  Optionally you can make a /home partition too.

---

### Post by bodhi.zazen on 2008-12-15
If gparted fails (and it may) and the disk is new, use fdisk :

[http://community.linux.com/howtos/Partition/partition-5.shtml](http://community.linux.com/howtos/Partition/partition-5.shtml)

[http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

---

