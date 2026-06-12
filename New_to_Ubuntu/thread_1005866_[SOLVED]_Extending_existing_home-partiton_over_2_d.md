---
title: "[SOLVED] Extending existing /home-partiton over 2 disks (LVM2)"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by pwicken on 2008-12-08
I am stuck. and I feel stupid. I have been reading tutotials, how-tos and forum postings about LVM2, without getting confident enough to procede. I have Ubuntu 8.10 64-bits and two disks each 750 GiB. My 1st disk is partitioned without LVM as shown:

/dev/sda1	ext3		/		 48,91 GiB	boot
Not partitoned					100,17 GiB	
/dev/sda2	extended			549,55 GiB
    /dev/sda5	swap				  4,86 GiB
    /dev/sda6	ext3		/home		544,69 GiB

What I want to do is to extend the 544 GiB on my /home partition over the entire 2nd disk so I get a continous /home of approx. 1.4 TB, without erasing any data on my 1st harddrive.

Is this possible?
Could it be done without LVM? Just by creating a partition on sda2 and som clever fstab-tricks?

---

### Post by nhasian on 2008-12-08
it looks to me like you have two options.  you can:

1) simply mount the additional disk space in a new folder like /home2

or

2) backup your data and do a fresh installation so you can create a new LVM that spans both of your discs.

---

### Post by bodhi.zazen on 2008-12-08
You can do this with LVM.

You can also do this in a simpler way, is there some reason you "need" on large /home partition ?

IMO, make a data partition. Mount it in say /media/data

Then 

ln -s /media/data /home/user/data

change "user" to your log in name.

---

### Post by scorp123 on 2008-12-08
See bodhi's suggestion above. It's a very good idea. I personally do something similar, e.g. I have lots of huge disks mounted as /data, /data2, /data3 ... Underneath each of those mount points there is a directory that belongs to me, e.g.
[INDENT]/data/myuser
/data1/myuser
/data2/myuser
/data3/myuser
[/INDENT]
And inside those directories that belong to me I keep all my stuff:
[INDENT]/data/myuser/Music
/data2/myuser/TV_Shows
/data3/myuser/Movies
... [/INDENT] Now if I want those directories to appear underneat my /home/ directory, I simply link back to it. So inside my /home/myuser I have links that go to those locations mentioned above:
[INDENT]/home/myuser/Music  -->  /data/myuser/Music
/home/myuser/Videos -->  /data2/myuser/Videos
/home/myuser/Movies  -->  /data3/myuser/Movies
... [/INDENT]

Like this it does not really matter how big or how small my /home directory is. From the point of view of all applications all those files are underneath /home/myuser ...  If I need more space I simply add more disks (SATA or USB, or Firewire ...) and then link the new volume back to my home, so I don't have to worry about relocating my files and everything else or resizing partitions.

Also: With above scenario: If one of the disks fails or if anything else weird happens there is a very high chance that you will easily be able to get all the data out. Or at least most of it.

With LVM's however matters get very complicated. If one of the disks fails, technically the entire volume as such has failed too. And you'll only be able to access one broken half of a file system which means there could be lots of other side effects (e.g. broken files because one half of a file is here, the other half is on the platter that just failed ...). Talking out of experience I'd say that: yes, LVM's can solve a lot of problems ... but they sure also create a lot of new ones.

In absence of any mirroring mechanism (e.g. RAID setup) I personally prefer not to use LVM's that span across multiple harddisks.

If you really want to use LVM here is a tutorial from IBM that should cover all the basics:

Learning Linux LVM, Part 1, by IBM:
[http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)

Learning Linux LVM, Part 2, by IBM:
[http://www.ibm.com/developerworks/library/l-lvm2.html](http://www.ibm.com/developerworks/library/l-lvm2.html)

---

### Post by pwicken on 2008-12-08
Thank you all. I'll try the symlinks. Adding complexity to the filesystem without enhancing security is probably not a godd idea anyhow.

---

