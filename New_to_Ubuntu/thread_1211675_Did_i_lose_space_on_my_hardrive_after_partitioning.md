---
title: "Did i lose space on my hardrive after partitioning?"
date: 2009-07-12
forum: New to Ubuntu
---

### Post by Darkoblivion2 on 2009-07-12
Hi all, ok soooo heres the scenario...

i just bought and pieced together a new computer from scratch.

i have a               [Western Digital Caviar Black WD1001FALS 1TB 7200 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822136284")

and when i installed ubuntu earlier this weekend, i partitioned 500gbs for ubuntu, and 25gbs for swap... buuuut i didnt do anything with the other 475gbs... i just left it as "free space"

how do i figure out if i can access this "free space" thru nautilus?

did partition it wrong? should i do a reinstall?

the reason i ask, is because i was under the impression that when u partition your hard drive into separate partitions, u can access those places like separate hard drives...

plz help me!

tyvm!

---

### Post by iponeverything on 2009-07-12
You are not going to see the free space in nautilus unless you turn the free space into a formated partition.

---

### Post by anystupidname on 2009-07-12
System>Administration>Partition Editor

Free space can typically only be used once you've partitioned it.

A 25GB swap partition is like you living in a mansion with 25 rooms. You'll never use them all... Generally 1.5 times the amount of RAM is recommended and I bet you have under 4GB of RAM.

---

### Post by Darkoblivion2 on 2009-07-12
> **anystupidname said:**
> System>Administration>Partition Editor

Free space can typically only be used once you've partitioned it.

A 25GB swap partition is like you living in a mansion with 25 rooms. You'll never use them all... Generally 1.5 times the amount of RAM is recommended and I bet you have under 4GB of RAM.

u bet wrong sir!

im pushing 8! haha!

ok, on topic...

so i need to partition that free space, and i will be able to see it as "another" hard drive?

---

### Post by Darkoblivion2 on 2009-07-12
System>Administration>Partition Editor

i dont have editor under admin...

---

### Post by rockerphil on 2009-07-12
if by chance you don't have Gparted installed (which i highly doubt if you're using Gnome) just run this command to install it

```
sudo apt-get install gparted
```

then to make it easier just run this command to start the parition editor

```
sudo gparted
```

you should be able to see the unpartitioned space and be able to format it to whatever you like, i'd recommend something native, either ext2 or ext3. hope this helps,

Phil

---

### Post by austinpsycho on 2009-07-12
try gparted ;)
[edit]oop; looks like somebody got to it before me ;)

---

### Post by anystupidname on 2009-07-13
> **Darkoblivion2 said:**
> u bet wrong sir!

im pushing 8! haha!

ok, on topic...

so i need to partition that free space, and i will be able to see it as "another" hard drive?

My bad... I didn't realize gparted wasn't installed by default.

For swap size I generally go off of something like this:

0.5 GB RAM 1 GB - 2 GB Swap Space
1 GB RAM 2 GB - 3 GB Swap Space
2 GB RAM 2 GB - 3 GB Swap Space
3 GB RAM 3 GB Swap Space
4 GB RAM 4 GB Swap Space
8 GB RAM 4 GB Swap Space
16 GB RAM 8 GB Swap Space

But I suppose if you have some kind of VM server or number crunching machine you might want something different...

---

