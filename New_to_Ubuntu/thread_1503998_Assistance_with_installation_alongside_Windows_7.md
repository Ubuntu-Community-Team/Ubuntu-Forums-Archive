---
title: "Assistance with installation alongside Windows 7"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Toucan Sam on 2010-06-07
I am currently trying to install Ubuntu 10.04 alongside Windows 7 on a RAID system, but I am running into a few problems. I tried using gparted to partition, but, alas, I received an error of "Could not stat /dev/isw_dacddfbefe_Sam1 --- No such file or directory"
Then, I went into the terminal and used mke2fs -t ext4 /dev/mapper/isw_dacddfbefe_Sam1
But all I got was:
"ubuntu@ubuntu:~$ sudo mke2fs -t ext4 /dev/isw_dacddfbefe_Sam1
mke2fs 1.41.11 14-Mar-2010)
Could not stat /dev/isw_dacddfbefe_Sam1 --- No such file or directory

The device apparently does not exist; did you specify it correctly?"

Halp?

:cry:

---

### Post by Mariane on 2010-06-07
You don't have to partition before installing. Burn a Ubuntu install CD and boot from it. It will give you the option to partition automatically using grub. 

Mariane

---

### Post by Toucan Sam on 2010-06-07
Perhaps I should've said I've already tried that.

---

### Post by barney385 on 2010-06-07
What kind of RAID array are you using? Is it 0 or what?

Makes a big difference on how to help you.

---

### Post by Toucan Sam on 2010-06-07
I'm going to have to go with 0. Because, at least, that's the one I'd be installing on, right? :???:

*Sigh*

I should be able to find it in the BIOS.

But where?

I'm currently running a Lenovo W700.

---

### Post by Toucan Sam on 2010-06-07
So I referred to [http://blog.taragana.com/index.php/archive/how-to-remove-stop-software-mdadm-raid-array-on-linux-cent-os]("http://blog.taragana.com/index.php/archive/how-to-remove-stop-software-mdadm-raid-array-on-linux-cent-os/")
And used:
cat /proc/mdstat
And received:
Personalities : 
unused devices: <none>
Perhaps I'm just off on the command. I've been researching this all day.

---

### Post by Mark Phelps on 2010-06-08
> **Toucan Sam said:**
> I am currently trying to install Ubuntu 10.04 alongside Windows 7 on a RAID system, :

Can't help you with the RAID issue, but I can tell you to NOT use the Ubuntu installer to resize your Win7 partition(s).  This runs the risk of corrupting said partitions and rendering Win7 unbootable.

Instead, use the Win7 Disk Management utility to shrink the OS volume to make room for Ubuntu.  Then, you probably need to use the Alternate CD to do manual partitioning -- because it understands RAID systems.

---

### Post by Toucan Sam on 2010-06-08
I think it is much more simple than that.

I really don't care much for my RAID system, but disabling it would be a pain in the :mad:, and I would have to mess with the hardware myself, or pay someone else to do it.

So I tried something alternative. Deleting the RAID system left me with two HDDs, and, of course, neither of them worked. So I took half of each of them and made two separate drives.

Which has worked in the past.

It seems like it would be easy enough to install **one** OS on **one** of the drives.

---

