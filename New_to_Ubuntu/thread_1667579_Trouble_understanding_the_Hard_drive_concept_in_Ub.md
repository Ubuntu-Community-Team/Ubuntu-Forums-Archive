---
title: "Trouble understanding the Hard drive concept in Ubuntu"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by E-babe on 2011-01-15
I have hard time looking at my C drive ! I used windows for 20 years so i don't understand how ubuntu looks at my harddrive in many partitions, where in windows i only have 1 C drive and 1 recovery drive for manufacturer's files. Can anyone clarify how it works?

and does it have to be "mounted" every time i want to access it? 
Thanks for the help guys.

---

### Post by cottfcfan on 2011-01-15
Try installing Gparted and you will see when you open it how your drive is partitioned. If you used a standard install, you will just have 2 partitions, your main system & a swap area.
 And yes all partitions you access will have to be mounted first.
That can be as simple as right-clicking and mount though.

---

### Post by HermanAB on 2011-01-15
It actually works exactly the same as in Windows, just a little simpler.

In Windows, a pre-installed desktop machine usually has the hard disk partitioned in two: A small recovery partition and a large data partition.  The large partition is mapped to drive letter C:.  All your subdirectories, then form a tree with letter C: as the tree root.  

If you would map a second drive, for example the CDROM, it normally gets the root name D: and all the files and things on it then forms a second tree from that point on.

In Linux, the file system has only one tree root. When you want to mount a second drive, it gets mounted in one of two places: /media (removables) or /mnt (fixed, bolted down disks) and it then simply becomes part of the big tree.

Since about the year 1998, Windows can do the same and can also map disks anywhere, just like Linux, but it is usually only done on servers, not on desktops.  So, there isn't really much of a difference between Windows and Linux in this regard.

---

### Post by Vaphell on 2011-01-15
when you think about root dir of linux, you can compare it to the windowsy 'computer' place where all drives and other devices are listed. In that context C: is a child of 'computer' with no special meaning, one of potentially many items listed there.
Same thing in linux - there is that idea of a single abstract tree and partitions are simply mounted somewhere in that tree, usually in /mnt or /media (but it can be changed)

---

### Post by Rubi1200 on 2011-01-15
This has a nice explanation of the file-system on Linux:
[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

---

### Post by Chris Edgell on 2011-01-15
E-babe, 

That is such a cute name...

I am so glad you asked your question, it is an area I have struggled with and then just put off even trying to understand.  This sheds quite a bit of light on the concept.

This is the very concept I needed to even begin to understand to be able to put to operating systems in side-by-side; as it is I have just put everything in "wall-to-wall" ... that is to say, "cover the entire disk".

---

### Post by QLee on 2011-01-15
I agree with Chris Edgell, I too think you've chosen a cute nick.

[QUOTE=E-babe]
I have hard time looking at my C drive ! I used windows for 20 years so i don't understand how ubuntu looks at my harddrive in many partitions, where in windows i only have 1 C drive and 1 recovery drive for manufacturer's files. Can anyone clarify how it works?[/QUOTE]

With your Windows install, you have a simple setup. In Windows if you had more than one drive (in this case, since Windows considers any partitions it can read as separate drives, if you had more than one partition formatted as a type Windows could read you would show additional drives as drive letters.)

So you could have folders on C drive and if you had another drive you could have folders on it too. Those two distinct drives would show in the filesystem.

In a Linux type of filesystem, there is just one big filesystem. You may to choose to have as many different partitions you want (or as few) and specify where in the filesystem each one is located (mounted). You set it up the way you want it with fstab (file system table), locating things at the mount points you choose and then, once the options are set, you don't have to figure out anything about the filesystem except where you want a file to be in the filesystem. The fstab is read at boot time and mounts the drives it can find from the list. 

You can put the folders you want into any location that you have write access to in the filesystem (usually this is your home folder or some folder in your home or some location mounted in such a way that you have access).

[QUOTE=E-babe] and does it have to be "mounted" every time i want to access it?
Thanks for the help guys.
[/QUOTE]

Yes. Windows automagically mounts the "drives" for you, according to a set of rules.

With the Linux filesystem you choose where "drives" are mounted and even if "drives" are mounted on the filesystem the system is using. But they are not seen as drives any longer, they are just locations in the filesystem, names (sometimes people choose names like drive names or labels but something like drive D or E on Windows could be mounted in a location named "data" in your home folder on Ubuntu) Yes, you do have to have things mounted to act on them. Except filesystem checks, you do want to be unmounted for a filesystem check on a partition.

---

