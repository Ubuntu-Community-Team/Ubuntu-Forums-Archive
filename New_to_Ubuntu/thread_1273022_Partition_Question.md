---
title: "Partition Question"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-09-22
Hello,

Could someone explain how the partitions work?

I have a 120 GB hard drive, when I installed Ubuntu Jaunty, I gave it 40 GB.

I looked at GParted and it shows 80 GB for XP, called /dev/sda1.

There is a 4.01 GB partition called /dev/sda6, linux-swap.

Then there is a 31.12 GB one called /dev/sda2, extended.

There is one that looks like it is inside the 31 GB one, and is a 27.11 GB partition, /dev/sda5.

Thank you.

---

### Post by tgeer43 on 2009-09-22
It's pretty straightforward.
The primary partition is sda1 which contains XP.
The extended partition is sda2 which contains sda5 for Ubuntu and sda6 for the Linux swap file.
Don't expect them to add up to exactly 120GB, they won't.

tgeer

---

### Post by kansasnoob on 2009-09-22
If you install gparted:

```
sudo apt-get install gparted
```

it'll show up in System > Administration > Partition editor. Gives you a nice gui view:

[ATTACH]129430[/ATTACH]

---

### Post by barnaclebill18 on 2009-09-22
The reason I am asking is I was thinking of making a separate home partition and am trying to get more information, I don't understand the extended partition, the linux-swap appears to be separate from the extended one.

---

### Post by barnaclebill18 on 2009-09-23
> **kansasnoob said:**
> If you install gparted:

```
sudo apt-get install gparted
```

it'll show up in System > Administration > Partition editor. Gives you a nice gui view:

[ATTACH]129430[/ATTACH]

Thanks, I already have it and also a live CD of GParted.

---

### Post by tgeer43 on 2009-09-23
> **barnaclebill18 said:**
> The reason I am asking is I was thinking of making a separate home partition and am trying to get more information, I don't understand the extended partition, the linux-swap appears to be separate from the extended one.
It might appear that way but 27.11+4.01=31.12, does it not?
You're trying to make things more complicated than they really are. If you just want to create a separate partition for /home and your disk is currently fully allocated then just use Gparted to shrink one of the existing partitions then use the newly unallocated space to create a new partition for /home.

tgeer

---

