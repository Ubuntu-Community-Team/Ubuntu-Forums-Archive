---
title: "Resizing the Partition: How do I do it ?! :S"
date: 2009-03-26
forum: New to Ubuntu
---

### Post by Ben Crisford on 2009-03-26
Hey, last night I installed jaunty just to sort of check it out.  But as I was only sort of "checking it out", because my partition is very cluttered, I only gave it about 6/7 GB.

Now however I want to give it tons more space...  But how...

I have space to spare on ubuntu *and* vista (especially vista), and I want to re-size my partition.

But I don't know how :s.

Please help, i've been tearing my hair out all day.

---

### Post by cariboo on 2009-03-26
I would suggest using Vista's disk management software to resize it's partition first, then use gparted to resize your Ubuntu partition. Boot the LiveCD then go to System-->Administration-->Partition Editor and resize the partitions. Make sure you backup important data first.

Jim

---

### Post by kansasnoob on 2009-03-26
> **cariboo907 said:**
> I would suggest using Vista's disk management software to resize it's partition first, then use gparted to resize your Ubuntu partition. Boot the LiveCD then go to System-->Administration-->Partition Editor and resize the partitions. Make sure you backup important data first.

Jim

+1! I've found it's always best to use Vista's own partitioning tools to resize Vista's partitions. This should give you a general idea of "how to":

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

As far as resizing and/or moving Ubuntu partitions you'll first want to make a plan. If you haven't already done so install gparted either from Synaptic or go to terminal and:

```
sudo apt-get install gparted
```

then go to System > Administration > Partition Editor. ***Now, you won't want to use that to do any resizing because partitions will be mounted - for that you'll want to use your Ubuntu Live CD!***

Anyway, with gparted installed you could post a screenshot:

[ATTACH]107692[/ATTACH]

You can see in mine that:
sda1 = XP
sda2 = an extended partition that contains all of my Linux OS's
sda5 = Hardy
sda6 = SWAP (shared by all Linux OS's)
sda7 = Jaunty /
sda8 = Jaunty home
sda9 = Mint 6 /
sda10 = Mint 6 home

There are a few basic things to consider:
(1) You can't exceed the 4 primary partition limit! Thus the need for an extended partition.
(2) Resizing or moving SWAP will result in some UUID problems - easy to deal with but you should be prepared.
(3) Don't "paint yourself in a corner"! Look here:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

(4) Back up! Gparted is great and I've had very few problems, but things can go wrong! Such as a power outage in the middle of repartitioning!

---

### Post by sandyd on 2009-03-26
> **kansasnoob said:**
> +1! I've found it's always best to use Vista's own partitioning tools to resize Vista's partitions. This should give you a general idea of "how to":
 
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)
 
As far as resizing and/or moving Ubuntu partitions you'll first want to make a plan. If you haven't already done so install gparted either from Synaptic or go to terminal and:
 
```
sudo apt-get install gparted
```
 
then go to System > Administration > Partition Editor. ***Now, you won't want to use that to do any resizing because partitions will be mounted - for that you'll want to use your Ubuntu Live CD!***
 
Anyway, with gparted installed you could post a screenshot:
 
[ATTACH]107692[/ATTACH]
 
You can see in mine that:
sda1 = XP
sda2 = an extended partition that contains all of my Linux OS's
sda5 = Hardy
sda6 = SWAP (shared by all Linux OS's)
sda7 = Jaunty /
sda8 = Jaunty home
sda9 = Mint 6 /
sda10 = Mint 6 home
 
There are a few basic things to consider:
(1) You can't exceed the 4 primary partition limit! Thus the need for an extended partition.
(2) Resizing or moving SWAP will result in some UUID problems - easy to deal with but you should be prepared.
(3) Don't "paint yourself in a corner"! Look here:
 
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)
 
(4) Back up! Gparted is great and I've had very few problems, but things can go wrong! Such as a power outage in the middle of repartitioning!
 
run gparted on LiveCD.
 
you cannot resize your partition while the OS is writing data to it.

---

### Post by kansasnoob on 2009-03-26
> **carlee said:**
> run gparted on LiveCD.
 
you cannot resize your partition while the OS is writing data to it.

Did you read the part in bold print where I said, "Now, you won't want to use that to do any resizing because partitions will be mounted - for that you'll want to use your Ubuntu Live CD!"

---

### Post by |{urse on 2009-03-26
just an fyi, do it with the livecd.

:lolflag:

---

### Post by kansasnoob on 2009-03-26
Can I get a +1 from anyone for suggesting one plan their partitioning before jumping in!

Or maybe we should just suggest going 'willy-nilly" and if it blows up, we can say, "oh well"!

---

