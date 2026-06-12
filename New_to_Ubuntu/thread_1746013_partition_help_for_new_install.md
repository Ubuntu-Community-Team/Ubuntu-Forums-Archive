---
title: "partition help for new install"
date: 2011-05-01
forum: New to Ubuntu
---

### Post by natman on 2011-05-01
Hi,
I am planning on installing kubuntu 11.04. My new hp laptop has the following already on the HDD ( 4 partitions )
1: c:\ 441 GB
2: d:\ recovery 23 GB
3: HP_tools 103mb
4: System 199mb

I made my back up discs, so im safe to delete the recovery partition, i will shrink C and leave system and hp_tools ( since i dont know what they do ). So then i need to make / and /home and swap. Is it ok to have them as non primary partitions - will there be any performance issues ( eg boot  up time )?
Also can i write to the C:\ drive ( ntfs ) from Linux?

Thanks:

---

### Post by An Sanct on 2011-05-01
Disks can only have 4 primary partitions.

If you want to install in the place of "d:", simply delete that partition from a Live CD/USB or any other partitioning tool.

Do ***NOT***, repeat ***NOT*** *make* /, /home and swap partitions if you do not know what you are doing, let the install manage that for you. In the installation you can also select advanced partitioning and do that there.

I don't know why people think, they have to do any partition by themselves ....
Please watch [this YouTube howto]("http://www.youtube.com/watch?v=SrWqKbqDQpU&feature=related"), its 8 minutes and is straight to the point and accurate, avoid others, like the one from TechHarvest ... no link here, I don't link to garbage how-tos, that make me angry...

Also, take a peak at this [thread]("http://ubuntuforums.org/showthread.php?t=1735964"), someone did just the same thing :)

PS. IMHO 11.04 is not "*there*" yet ... but that is just my opinion, do as you wish ;)

---

### Post by natman on 2011-05-01
Thanks,
But can anyone answer my questions, will my plan compromise boot time or any other system performance and can i write into ntfs from C:\

---

### Post by slashwannabe94 on 2011-05-01
Natman, 

Yes you can write to NTFS from Linux, as linux recognizes NTFS partitions. Although Windows cannot see Linux as it's stored on an ext3 or ext4 partition. 

Correct me if i'm wrong, but since you are planning to dual boot both operating systems you should use the partition manager on the live disc instead of doing it manually. If you need to do it manually i suggest you read up more on partitioning. 

And as for your system boot performance i don't think that having two operating systems will affect your speed. Boot time is determined by your hardware, i.e. CPU, RAM and your HDD interface, e.g. "SATA, SATA2, IDE or Solid state". 

Hope this helped dude.

---

### Post by hictio on 2011-05-01
Here is a nice (and up to date) article on the pro and cons of partitioning nowadays.

[Making the Case for Partitioning](http://administratosphere.wordpress.com/2011/04/24/making-the-case-for-partitioning/)

Personally, on my boxes, laptops, I don't partition (other than swap) mostly because I want to max the HDD space to the limit, specially with the minuscule SSD ones.

YMMV :D

---

### Post by srs5694 on 2011-05-01
> **slashwannabe94 said:**
> Yes you can write to NTFS from Linux, as linux recognizes NTFS partitions.

Although this is true, I *strongly* recommend against routinely writing to the Windows boot (C:) partition from Linux, for two reasons:


[list]
[*]Linux doesn't understand Windows' security measures, which means that if you give yourself write access to NTFS, it becomes very easy to accidentally delete or overwrite some critical file that Windows wouldn't allow you to touch if you were booted in Windows.
[*]Although the NTFS-3g drivers that Ubuntu uses have gotten favorable anecdotal reports for reliability, it's hard for me to believe that they're as reliable as Microsoft's own drivers. (NTFS is a proprietary filesystem; NTFS-3g was written by reverse engineering.) If there's a bug lurking in the NTFS-3g drivers, it could easily wipe out the whole partition.
[/list]


Instead of writing to C: from Linux, I recommend creating a shared-data/data-exchange partition. I'd use FAT for this if you can live with the 4 GiB file-size limit of FAT; otherwise, NTFS is probably the best choice, although a case could be made for ext3fs with suitable drivers in Windows.

---

