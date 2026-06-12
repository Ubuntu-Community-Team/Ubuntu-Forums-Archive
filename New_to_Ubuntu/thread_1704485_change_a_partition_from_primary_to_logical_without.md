---
title: "change a partition from primary to logical without  erasing data"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by kiraku on 2011-03-10
Hi:

Somebody knows if changing the type of partition from primary to logical without erasing the data might affect the performance of it or how interact with the otherones and the os too (in my case windows 7)

I'm asking this because my pc came with 4 primary partition, and i want my last solution to be erasing one of the partition in order to install linux on it....

greettings

---

### Post by Hedgehog1 on 2011-03-10
kiraku,

While we cannot change a partition from primary to extended, we can do a little fancy foot work so you don't lose any data.

We need to get a look at your disk partition layout and see where we have 'wiggle' room.

Please boot off of your Ubuntu LiveCD or LiveUSB, select 'try' then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by oldfred on 2011-03-10
See also this thread:

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)

---

### Post by srs5694 on 2011-03-10
> **Hedgehog1 said:**
> While we cannot change a partition from primary to extended, we can do a little fancy foot work so you don't lose any data.

An extended partition is a special type of primary partition that holds logical partitions. Turning a primary partition into an extended partition would be extremely destructive, but turning a primary partition into a logical partition (if possible) would not be. Kiraku used the terminology correctly, and I just want to clarify this point so as to avoid confusing others.

> We need to get a look at your disk partition layout and see where we have 'wiggle' room.

Please boot off of your Ubuntu LiveCD or LiveUSB, select 'try' then:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```

Please make that:

```
sudo fdisk -lu
```

The "u" option changes the units from the imprecise cylinder units to the much more precise sector units. This detail can be critical because it determines whether a partition can theoretically be turned from primary to logical.

> Then copy the text from the output and paste it into your next post.

Please do so between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This will improve legibility.

[quote=oldfred]Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)[/quote]

What I posted in that thread is indeed the best way to deal with the issue, at least at the moment. Converting from one or more partitions from primary to logical is at least a theoretical possibility, but AFAIK no Linux tool currently makes this easy. (I'm working on one that will, but only if the partitions are laid out in certain ways.)

---

### Post by Hedgehog1 on 2011-03-10
srs5694,

I was thinking something much less sophisticated: Clonezilla **sda3** & **sda4** to files stored in **sda2**, make new extended **sda3**, put back **sda3** & **sda4** as **sda5** & **sda6**, then fill the rest of the extended **sda3** partition with Ubuntu's **sda7** & **sda8**.

OK, now that I have typed it out - it doesn't look so easy.

***The Hedge***

I will just go curl up in a ball, now.

---

### Post by kiraku on 2011-03-11
Here it goes:

```

Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros, 1250263728 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x09168887

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2          409600  1206485771   603038086    7  HPFS/NTFS
/dev/sda3      1206487040  1250050047    21781504    7  HPFS/NTFS
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)


```For the record:

- sda1 is a "system partition" that apparently boot the system, or something like that
- sda2 is the "C:" partition with windows 
- sda3 is the recovery partition
- sda4 called HP_TOOLS... this is the one i'd like to change into logical...

And i'd like to add that there is a windows software that apparently do the change very easily, so that why i'm finding out if this change might cause some sort of problem...

---

### Post by Hedgehog1 on 2011-03-11
-delete-

---

### Post by oldfred on 2011-03-11
Be sure that the windows software is not changing it from basic to dynamic. That is a windows only proprietary logical volume manager that is compatible with just about nothing including some windows utilities.

---

### Post by Hedgehog1 on 2011-03-11
-delete-

---

### Post by Hedgehog1 on 2011-03-11
-delete-

---

### Post by kiraku on 2011-03-11
Thanxz hedgehog1, but i already knew how to do that... and as i said in my first post, i want this (i.e, erase one partition) be my last solution...
[U]
[]("http://ubuntuforums.org/member.php?u=1230016")[/U]

---

### Post by Hedgehog1 on 2011-03-11
kiraku,

The windows software that will convert primary in logical partitions, is it something like the product in the links below?

[change-partition-type]("http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm")

[partition-magic]("http://www.partition-magic-server.com/server.html")

This software it is not cheap, but is does offer a **powerful set of tools**.  The 'demo' mode does not let you actually make partition changes, sadly.  But for an IT Professional, this could be a real winner.

In your case, it offers the ability to both convert the **sda4** partition, or to merge **sda3** & **sda4** into a single **sda3** partition.  For what it costs, you can just by the Win7 disks, However.

You could move/expand the **sda3** partition using gparted, add the contents of **sda4** into **sda3** so you don't lose anything, and then delete and recreate **sda4** as an extended partition for your Ubuntu install.  *This, you could do for **free***.

***The Hedge***

:KS

---

### Post by kiraku on 2011-03-11
> **Hedgehog1 said:**
> kiraku,

The windows software that will convert primary in logical partitions, is it something like the product in the links below?

[change-partition-type]("http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm")

[partition-magic]("http://www.partition-magic-server.com/server.html")

This software it is not cheap, but is does offer a **powerful set of tools**.  The 'demo' mode does not let you actually make partition changes, sadly.  But for an IT Professional, this could be a real winner.

In your case, it offers the ability to both convert the **sda4** partition, or to merge **sda3** & **sda4** into a single **sda3** partition.  For what it costs, you can just by the Win7 disks, However.



Nop, it is none of them i think... it has a free licence from home use... it is called  MiniTool Partition Wizard Home Edition. However, i will check if i actually can do the change for free xD...

If I could, do you know of anything bad that could happen? would you recommend to do this? or do you prefer the option you give me... 

[QUOTE=Hedgehog1;10549649]

You could move/expand the **sda3** partition using gparted, add the contents of **sda4** into **sda3** so you don't lose anything, and then delete and recreate **sda4** as an extended partition for your Ubuntu install.  *This, you could do for **free***.

[\QUOTE]

I think that this is a good option too...

Anyway, thank you very much for your help...

---

### Post by srs5694 on 2011-03-11
> **kiraku said:**
> Here it goes:

```

Disco /dev/sda: 640.1 GB, 640135028736 bytes
255 cabezas, 63 sectores/pista, 77825 cilindros, 1250263728 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes
Tamaño E/S (mínimo/óptimo): 512 bytes / 512 bytes
Identificador de disco: 0x09168887

Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/sda2          409600  1206485771   603038086    7  HPFS/NTFS
/dev/sda3      1206487040  1250050047    21781504    7  HPFS/NTFS
/dev/sda4      1250050048  1250261679      105816    c  W95 FAT32 (LBA)


```For the record:

- sda1 is a "system partition" that apparently boot the system, or something like that
- sda2 is the "C:" partition with windows 
- sda3 is the recovery partition
- sda4 called HP_TOOLS... this is the one i'd like to change into logical...

To convert a partition from primary to logical, at least one free (unallocated) sector must exist between the partition and the one that precedes it. Currently, you can convert either /dev/sda1 or /dev/sda3 to logical partitions, but not both; and converting /dev/sda1 would be extremely unwise, since Windows probably relies on it being logical to boot and/or to boot its recovery mode. Converting /dev/sda3 is probably safer; however, I don't know how the recovery tools will react if you do this, should you ever need to run them.

Because there's no gap between /dev/sda3 and /dev/sda4, you can't convert /dev/sda4 into a logical partition -- at least, not without doing further modifications. If there's sufficient free space on /dev/sda3, you could shrink /dev/sda3, which would create free space before /dev/sda4, enabling conversion of /dev/sda4 into a logical partition.

Do you want to do this so that you can create additional partitions for a Linux installation? If so, you'll need to resize, and perhaps move, other partitions. Specifically, you'll need to shrink /dev/sda2, since it's the only one with enough free space. From there, I see three good courses of action (and several others that are less appealing):


[list=1]
[*]Run the Windows tools to create recovery DVDs, delete /dev/sda3, create a new extended partition in its place, and create logical Linux partitions in the new extended partition.
[*]Convert /dev/sda3 to a logical partition, resize the extended partition that will be created in that process to fill the gap between /dev/sda2 and the new extended partition, and put the logical Linux partitions in the free space within the extended partition.
[*]Move /dev/sda3 earlier, shifting the free space from between /dev/sda2 and /dev/sda3 to be between /dev/sda3 and /dev/sda4, convert /dev/sda4 into a logical partition (which will then be possible), expand the resulting extended partition, and add new logical Linux partitions inside the extended partition.
[/list]


My recommendation is to do #1, mainly because recovery DVDs will work even if the hard disk dies completely. Without recovery DVDs, you won't be able to recover your Windows installation if the hard disk dies completely. (Of course, you could create the recovery DVDs and do #2 or #3 from the above list.) Doing #1 will also free up some space on the disk that you can devote to Linux.

Option #3 might be safer than #2 in the sense of there being less question about your ability to recover your system in the event of a massive Windows failure; but moving a partition is inherently risky, so there's a chance that you'll trash your recovery data on /dev/sda3 if you attempt #3.

Any of these options will require running several tools for manipulating disks. GParted is good for resizing and moving partitions, although it's safer to resize a Windows boot partition using Windows' own tools.

As to doing the actual conversion from primary to logical, my new program for this is [FixParts.](http://www.rodsbooks.com/fixparts/) The version you can download now is still officially in alpha test, but it seems pretty stable. I'm preparing a final release that I hope to get out this weekend, but I need to run some more tests, prepare the actual binary packages, and update the documentation. Unless you're desperate, I recommend you read the Web page but hold off on using it until the official first non-alpha release.

---

### Post by kiraku on 2011-03-12
thanxz [srs5694]("http://ubuntuforums.org/member.php?u=1032238"), i'm going to consider your suggestions... and your explanation about when can i change a partition to logical was really helpful...

---

### Post by srs5694 on 2011-03-12
FWIW, I've released the first non-alpha version of FixParts. It's numbered at 0.7.0, mainly just because it relies on the same code base as GPT fdisk, which I bumped up to 0.7.0 with this release.

---

### Post by panaut0lordv on 2012-04-06
Wow, man, I'm sorry for being necroposter but your tool is great, big thanks to you!
It took me about 2 minutes to download deb, check how this tool works, remount my USB drive and realise that primary partition is logical within nice extended partition now <3

Thank you so much for your work!

Cheers,
Michael

---

### Post by oldos2er on 2012-04-06
Closed, necromancy.

---

