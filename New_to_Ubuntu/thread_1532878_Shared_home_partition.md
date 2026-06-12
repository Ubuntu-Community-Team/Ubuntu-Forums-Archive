---
title: "Shared home partition"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by blairm on 2010-07-17
Hi,

Have bought a new laptop that came with Windows 7, and toying with the idea of dual booting Lucid with a shared home partition.
So two questions:

1) How diificult is it to create a shared home partition? And if I was to go the shared home route, am I still able to use ext4?

2) Have seen a lot of people saying Windows 7 and Ubuntu don't go together too well on dual boots - trouble booting into one or the other after the installation, sound vanishing in Windows 7 etc. Anything in particular I should watch out for?

Thanks,

Blair

---

### Post by Gone fishing on 2010-07-17
As far know there is no windows driver for ext4 there are 2 for ext3 I use ext2IFS which works well. However it doesn't work with ext3 partitions that Ubuntu creates as they use a slightly updated format. It does work with the partitions that the gparted live CD creates.

So if you create your home partition using a gparted live CD and install ext2IFS in windows it will be accessible and works well.

I dual boot with Windows 7 I resized Win 7 using gparted and had no problem but I have heard it is better to resize Windows from within windows using the disk management tool.

---

### Post by candtalan on 2010-07-17
>  How diificult is it to create a shared home partition? And if I was to go the shared home route, am I still able to use ext4?


Shared with Windows?

Ubuntu does not usually create a *partition* for Home, although it can be done easily. Your stuff will be in 
/Home/username which is a directory (ie folder)
including some 'hidden' files relevant to your configuration.

The folder will have permissions which I expect can be set to enable others to use them ie be shared. However, being able to view and use these from Windows may not be easy, as you suggest, ext4 is not liked by Windows I expect. 

Anyway I would not want to give Windows any access to my Ubuntu ..... 

Have you considered just creating a partition, separate from Windows and Ubuntu, formatted to something suitable, and use the new partition as a sharing partition, because it can be mounted and used in both systems? I routinely do this even without having Windows at all, because I can then run a number of differing systems and still access my favourite information on my 'data' partition. In my case I use a separate hard drive containing the data.
partition.
hth

---

### Post by mapes12 on 2010-07-17
Try these links:-

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

[http://members.iinet.net.au/~herman546/p10.html](http://members.iinet.net.au/~herman546/p10.html)

Mark

---

### Post by dv3500ea on 2010-07-17
If you choose manual partitioning in the installation, you can choose what partitions to create, their mount point and what filesystem to use. You will need a 'root' partition (mounted at '/') and a 'home' partition (mounted at '/home'). 

FAT32 would be the most cross compatible filesystem although there is a 4GB file size limit. NTFS is what Windows uses by default and is supported in Linux (although some have had problems with it). Ext2/Ext3 are supported perfectly by Linux but you need to install extra software (as mentioned above) for them to work in Windows. (In my experience this hasn't worked). Consider creating an extra 'share' partition with the FAT32 file system so that you can share files to Windows without messing up your user settings (which are also in your /home folder).

 I can't remember, but you may have to create the partitions first using the partition manager.

---

