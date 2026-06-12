---
title: "OT:  Is Mandriva Linux more windows friendly"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by xiongnu on 2010-12-08
hi, guys

a little bit off topic here:
I'd like to setup a dual boot on my windows XP PC.  
But I heard that Ubuntu is not very windows-friendly.  In other words:  It doesn't like to share hard drive space with windows. 

What i currently have is 640GB sata hard drive divided into 4 partitions (all NTFS FS). The windows XP os is on the primary  C:\ partition, with mostly movies/games/mp3 music occupy the rest 3 partitions). 


i used Mandrake linux in the past and had no problem with dual-boot setup with windows.  so just wondering how to properly setup a dual-boot system.

---

### Post by ajgreeny on 2010-12-08
> But I heard that Ubuntu is not very windows-friendly.  In other words:  It doesn't like to share hard drive space with windows. Where did you hear this?  It is definitely incorrect!

I had Windows XP dual booted with Ubuntu right up to the point that I put Karmic on my machine, then decided that windows was simply taking up useful space as I only ever booted to it in order to update the viruc checker, never to actually use it for anything.  Not once in those 4 or 5 years did I have any problems related to the dual boot, and i think the thousands and thousands of other dual booters would also agree.

I suggest you defrag your windows a couple of times, then shrink the partition with gparted on the ubuntu live CD.  Keep windows as first OS on the disk, and do not try to move the partition to the right, just shrink it.  I would now reboot to windows just to make sure all is well.

Finally install ubuntu, and at the partitioning page, choose manual partitioning for safety's sake, and you can then make sure you only use the unallocated space on the disk for your new partitions.

If you have room, make one extended partition using the whole of the unallocated space, and within that partition make a root partition of about 10GB, a swap of about 2GB, or up to 4GB if you want to hibernate, and all the rest as a /home partition.  Make sure grub is installed onto /dev/sda which it will be by default, not to a partition.

> To elaborate this is because Ubuntu and most linux distributions  use the EXT4 (or ext3) file system while windows uses NTFS. It is  possible to install ubuntu on Fat32 and have it accessed from windows  but generally you will want to stick to EXT4 for linux.This is not a correct statement.  You can not install ubuntu or any other linux to a fat32 partition as linux depends upon various permissions for folders and files.  These permissions are not supported on fat32.

Linux and ubuntu can read and write to a fat32 partition, but only for data storage; it is not possible to put a root partition or any other of the OS partitions on fat32; only a data partition can be fat32 and then mounted at boot time.

---

### Post by HermanAB on 2010-12-08
Linux is Linux is Linux...

However, the Mandriva wizards are much better than Ubuntu.  New Ubuntu users inadvertently zapping their Windows installs is still a common occurrence - something Mandriva licked way back in the previous century already.

---

### Post by xiongnu on 2010-12-09
I asked the question since i'm too afraid to mess up my existing windows partitions.

I intended to use this machine mainly as a file server instead of desktop since it stores most of my multimedia stuff.  and I hook it up directly with my wi-fi router and have it running most of the time. I ususally access it through windows RemoteDesktop or home networking from my laptop or other desktop.   But the problelm is that Windows XP crashed a lot on this machine, with the dreaded BSOD.  So I decided to add linux to it.  

I've done some readings and it now comes down to three choices:  Mandriva, Ubuntu, or CentOS.

any suggestions from you guys?

---

### Post by amjjawad on 2010-12-09
> **xiongnu said:**
> I asked the question since i'm too afraid to mess up my existing windows partitions.

You need to BACKUP everything as long as you're using Windows. In case something will go wrong, whether you're trying to install Linux or not, you'll be in the safe side.

> any suggestions from you guys?

I'd suggest you try the LiveCD. No need to install anything, just download Ubuntu or any other OS, burn the iso to a CD, make sure your machine boot from CD/DVD first and try that OS. That feature you can't find in Windows. After all, you could read a lot about Linux Distributions which are more than 500 (I guess) but the best to try that yourself.
I have tried a lot and I mean a lot but I like Ubuntu the most.

Good luck!

---

### Post by amjjawad on 2010-12-09
> **xiongnu said:**
> In other words:  It doesn't like to share hard drive space with windows. 

Linux uses totally different Filing System than Windows.
Linux could read/write to NTFS partitions by default (no need to do anything) while Windows can't by default.

Almost everyone here has Dual booting (Ubuntu with Windows XP or 7). I have two PCs, both with Ubuntu and XP. The best part is: Windows can't mess around with my Linux Partitions which is all what I need.
As for Linux/Ubuntu, I won't even think to use the partition where Windows is installed. I have lots of other partitions where I can use.
As long as each has its own partition with different FileSystem, you're safe especially if you know what you're doing :)

---

### Post by ScottyD135 on 2010-12-09
If you're considering Mandriva, you might like PCLinuxOS.  It works very well(excellent hardware support... things just work), but it's base desktop is KDE (if that matters to you).

I used it for a while and then ended back with Ubuntu.  The support community is MUCH more extensive!

---

### Post by cgroza on 2010-12-09
To share files between Ubuntu and Windows you may set up a shared partition, but take note that Windows will not be able to read the Ubuntu partition but Ubuntu will.

---

### Post by madjr on 2010-12-09
ubuntu is super windows friendly, you can even install ubuntu like a windows program with wubi and use the same partition for everything.

but i suggest just installing ubuntu normally and the other comments here

---

### Post by amjjawad on 2010-12-09
Since "friendly" has been mentioned many times here, I can't resist posting this great article:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

For quick reading, check:** Problem #5: The myth of "user-friendly"**

---

