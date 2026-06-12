---
title: "removing windows completely without losing data &amp; merge the remaining space in ubuntu"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by fuser312 on 2009-01-16
ok i am done with vista now. i have a 250 gb hdd, with 50 gb dedicated to ubuntu. i got only one drive for vista, and i want to save around 80 gb of contents from it and make it available for ubuntu. is it possible, i got no  external drive for any back up. please see if you could help.

---

### Post by drjonze on 2009-01-16
Vista has a partition editor (its in the control panel under System). You should be able to use it to shrink your Vista partition down to the size you want, then you'd have to use a Live CD or gparted in Ubuntu to make a partition for Ubuntu out of the new free space. As far as I know, you can't merge your existing Ubuntu partition with the new one you'd be making.

However, I would recommend strongly that you back up your files first. You'd have to burn the back up to disks if you don't have an external HD or another computer. It might be a lot if disks but then you can be fearless in tweaking your system.

Something else: my method wouldn't be removing Vista, you'd still have it, it would just be a lot smaller. If you want it gone but want to keep your files from it (music, pictures etc..) you'll have to burn them or save them on something.

---

### Post by cerealtx on 2009-01-16
depending on how many files u might just try transfering them all to ur ubuntu partion temporarily untill u can wipe windows

---

### Post by BDNiner on 2009-01-16
Well since you ubuntu partition is 50GB and you have 80GB worth of data then a straight copy would not work. You would have to use the partition editor like drjonze recommends or backup your data to external media like cerealtx recommends.

I personally would back up the data to and external drive just in case something goes wrong.

---

### Post by billgoldberg on 2009-01-16
The only option you got if you don't have any external hdd or dvd disk is repartition the drive.

You create a new 80-85gb parition and format it as fat32.

Boot into Vista and copy your files to the newly created parition.

The wipe the Vista parition using the same program you created the 80-85gb partition with (I recommend gparted (gnome parition editor), it's on the Ubuntu live cd).

Then merge the empty partition Vista used to be on with the Ubuntu partition.

You could the merge the 80-85gb parition with the main Ubuntu parition, or don't. 

You can always access those files, so merging those isn't really neccesary.

Note, this whole progress could easily take 10-30 hours and if something goes wrong, you lose everything.

Merging and resizing paritions is slooooooooooooooowwwwwwww.

It would be easier and a lot faster to just buy an external hdd (20 bucks for a 250gb one). Format all Vista partition and the Ubuntu one. Reinstall Ubuntu, put / (root) on the 50gb Ubuntu parition and put /home on the partition Vista used to be on.

---

### Post by mister_pink on 2009-01-16
Risky tactic, but you could do the following from a liveCD using the partition editor:

1. Delete everything you dont want from the vista partition.
2. Shrink the vista partition as much as you can, and expand the ubuntu partition to take the space.
3. Copy the data you want to keep from the vista partition to the now larger ubuntu partition.
4. Delete the vista partition altogether, and expand ubuntu to take all the space.

A couple of things to be aware of:

1. After changing your partitions you may no longer be able to boot as the grub hard drive references may be wrong. There are many guides for recovery grub, usually for after a windows install but still applicable here (eg [https://help.ubuntu.com/community/WindowsDualBoot#Recovering](https://help.ubuntu.com/community/WindowsDualBoot#Recovering) GRUB after reinstalling Windows )

2. All this moving data around can cause it to be corrupted slightly. You could perhaps checksum the data when you copy it from vista to ubuntu before deleting the windows partition. This could take a while. 

3. You could take this opportunity to set up a separate home partition for ubuntu, and put the new data there. Doesn't reduce the moving things around much, but it kills two birds with one stone if you fancy it. See [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sdowney717 on 2009-01-16
whatever you do get rid of windows filesystems, dont use ntfs and fat32. Use only linux filesystems.
I personally would move only the files I really wanted from the vista partition to the ubuntu partition. you likely have a lot of junk you dont need. Then use gparted partition editor to delete the windows partition and expand the linux partition. Or you could keep a separate home partition from the linux filesystem install. 
You likely will have to use the live cd to do this.

you can always backup and restore you home directory even if you did a total wipe and reinstall.
just a few steps and your backed up home will be up and running on the new install

---

### Post by redseventyseven on 2009-01-16
> **fuser312 said:**
> ok i am done with vista now. i have a 250 gb hdd, with 50 gb dedicated to ubuntu. i got only one drive for vista, and i want to save around 80 gb of contents from it and make it available for ubuntu. is it possible, i got no  external drive for any back up. please see if you could help.

To be completely on the safe side, I would strongly recommend buying an external hard drive. They're not hugely expensive - not compared to the cost you'd suffer if anything went wrong with your re-partitioning. And you can then use it for storage and backups afterwards. It's a worthwhile investment. Alternatively you can burn things to a bunch of DVDs, but that's very time-consuming.

---

### Post by SPARTAN-118 on 2009-06-27
Hi, sorry, I'm a total n00b at partitioning, I used WUBI to install ubuntu 9.04 (Jaunty Jackalope) and need to merge my remaining Windows space to Ubuntu until I can get an external hard drive. Originally, (as in, before I got Ubuntu) I was going to install the Windows 7 RC, so I was considering buying an EHDD anyway, but then I met Ubuntu.

So my question is: is there a GOOD tutorial out there that explains just HOW to edit the partitions using the LiveCD (via gpartedit, I'd assume)? I got a little confused by the fact that all the space is in MiB (Megabytes? MB? What's with the "i"?), not in GB. I have 5.3 *MB* (literally) of free space in Ubuntu - 6.4 GB in Windows. 

_How do I merge about 4.2 Gigs with Ubuntu and leave the remaining 2.2 GB for Windows? _

(The Windows space is for stuff I can't do in Ubuntu [unfortunately], such as creating awesome movies in Windows Movie Maker and playing games that my computer can [barely] run - ie Halo: CE.)

---

