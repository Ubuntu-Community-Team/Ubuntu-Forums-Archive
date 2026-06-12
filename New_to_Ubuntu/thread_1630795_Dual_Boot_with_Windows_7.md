---
title: "Dual Boot with Windows 7"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by shad0w7 on 2010-11-25
ok guys, im using windows 7.
I want to install ubuntu as a second operating system, and i have some questions.

1) how many partitions should i create?
some told me 3, /root, /home /swap_swap area, others told me 2,
/root, /swap_area. also  should i go for ext4 or ext3? they told me ext3 was recently updated and is better. What is better to do??

2)what is the best way to create a partition?
using partition magic? or the ubuntu installer? or the windows disk management?

3) do i need a swap area? some told me you don't need it. you just need only 1 partition. :S

that's all.

---

### Post by sikander3786 on 2010-11-25
Welcome to Ubuntu and the Forums :-)

> 1) how many partitions should i create?

At least 2. / and Swap partition.

/home is optional. It saves all your personal data and program settings/configuration. Handy to have a separate /home as it saves you the hassle of backing up/extracting data from the root partition if the OS gets borked. All you do is reinstall with leaving /home intact and you'll not lose your settings.

I would recommend that / be sized > 8 GB and formatted Ext4. Ext4 is updated version of Ext3 and is the default Filesystem on 10.10.

Swap needs to be RAM x 2.

> 3) do i need a swap area? some told me you don't need it. you just need only 1 partition. :S

Unless you've a huge amount of RAM and don't ever plan to hibernate your PC, you can do without swap. But I would recommend to create a Swap partition any way.

First of all, boot from an Ubuntu Live CD. Test all your hardware and also post the output of

```
sudo fdisk -l
```

You need to do that from Applications > Accessories > Terminal.

And how much RAM do you have?

If you need to shrink your Windows partition and free up some space for Ubuntu, I would recommend using the Windows partitioning tool for that. Otherwise you can create partitions with gparted, partition magic or the installer itself, whatever you prefer. But I would recommend using the installer in that case.

---

### Post by sanderd17 on 2010-11-25
1) that's up to you: for ubuntu, I use a 15 GB partition for the OS, a 2GB partition for swap and the rest for /home.

the advantages of splitting /home and / (the root partition) is that I can damage my ubuntu installation very hard without losing data because they are on a separate partition. I can also reinstall ubuntu without losing data.

2) If you have win7, shrink your partition with the build in tool of win7 and leave the rest unallocated. Once you install ubuntu, format the unallocated piece in different partitions.

3) swap is needed when you don't have enough RAM, or if you want to hibernate. If you don't hibernate and you have 3GB RAM or more, you don't need swap. (I have swap and I never hibernate and have 3GB of RAM)

---

### Post by shad0w7 on 2010-11-25
> **sanderd17 said:**
> 1) that's up to you: for ubuntu, I use a 15 GB partition for the OS, a 2GB partition for swap and the rest for /home.

the advantages of splitting /home and / (the root partition) is that I can damage my ubuntu installation very hard without losing data because they are on a separate partition. I can also reinstall ubuntu without losing data.

2) If you have win7, shrink your partition with the build in tool of win7 and leave the rest unallocated. Once you install ubuntu, format the unallocated piece in different partitions.

3) swap is needed when you don't have enough RAM, or if you want to hibernate. If you don't hibernate and you have 3GB RAM or more, you don't need swap. (I have swap and I never hibernate and have 3GB of RAM)

do i need to shrink my volume? can't i just create the partitions
using the ubuntu installer on the free space?
and /root and /home are automatically recognized?

---

### Post by sanderd17 on 2010-11-27
free space is not free, it's formatted in series of bits so the OS knows it's free. This format depends on the type (for windows moslty NTFS). Ubuntu needs ext3 or ext4, this is another format. For that reason, you need to shrink your NTFS partition(s) and put ext4 on the free space.

Since NTFS is property of ms, windows does a better job in handling NTFS, that's why it is better to shrink the NTFS with the windows tool. Once th partition is smaller, you can use the ubuntu live CD to format the (now completely) free space as ext4. Windows can't handle ext4.

---

### Post by admiralspark on 2010-11-27
I think it's probably safe to say that if your windows partition is less than 80% full, gparted will have no problem shrinking an NTFS partition and adding in the ext3/ext4 partitions all at once. I've used gparted on many systems, from a 40gb HD on an old desktop to my new laptop (500gb, had to shrink NTFS and then create new partitions inside an extended partition). They all worked with no hitch, which unfortunately can't be said for the precoded partition manager in the installer(s). 

Many people recommend a three-partition setup: / (root), /home and swap. You only absolutely need just a / partition, but if you want hibernation or have less than 1gb of ram you will want swap. Having a separate /home partition is handy for those who install Ubuntu and then upgrade three years later--however, most of us upgrade every new release (6 months), and if you use a /home partition you'll have to manually edit your desktop configuration files every time. For instance, on the move from 10.04-->10.10, the desktop theme changed, but with a /home partition you will be stuck with the old scheme until you manually remove the configuration files (TRUST ME, that can take forever if you don't know what to look for). 

Anywho, good luck! Report back when you get it installed!

---

### Post by sanderd17 on 2010-11-27
> **admiralspark said:**
> I think it's probably safe to say that if your windows partition is less than 80% full, gparted will have no problem shrinking an NTFS partition and adding in the ext3/ext4 partitions all at once. I've used gparted on many systems, from a 40gb HD on an old desktop to my new laptop (500gb, had to shrink NTFS and then create new partitions inside an extended partition). They all worked with no hitch, which unfortunately can't be said for the precoded partition manager in the installer(s). 

Many people recommend a three-partition setup: / (root), /home and swap. You only absolutely need just a / partition, but if you want hibernation or have less than 1gb of ram you will want swap. Having a separate /home partition is handy for those who install Ubuntu and then upgrade three years later--however, most of us upgrade every new release (6 months), and if you use a /home partition you'll have to manually edit your desktop configuration files every time. For instance, on the move from 10.04-->10.10, the desktop theme changed, but with a /home partition you will be stuck with the old scheme until you manually remove the configuration files (TRUST ME, that can take forever if you don't know what to look for). 

Anywho, good luck! Report back when you get it installed!

Back when I had windows (it was Vista), the home version didn't have such a tool, so I did it too with Gparted. But I've heard from other guys on this forum that windows can handle NTFS better, I believe this, so I pass it on.

about the /home, going to 10.10, I deleted all settings before I upgraded, because I wanted the new themes and fresh profiles on apps. It is not that difficult and a fresh install is less likely to break. My way to upgrade is also different than most others.

In fact, I always have a dual boot with 2 linuxes. 1 which I use, and an other one for the case the first breaks (I know, I experiment too much, sometimes I even try to break it on purpose, it's the only way to learn). When I install the upgrade, I install it instead of the unused linux. That way, I can fall back to my previous if I need to.

If you don't experiment, you don't need a dual boot or even a separated /home but I find it handy.

---

