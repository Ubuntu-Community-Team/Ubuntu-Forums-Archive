---
title: "setup a SEPARATE DATA PARTITION,ubuntu FRESH INSTALL,single boot"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by steninj on 2011-04-20
hey all..

i am about to do a fresh installation of ubuntu 10.10(or 11.04)

what i need is,

to keep all my music,movies videos etc in a separate partition
so that i can keep all these even in case of  further installations...

i don't want this partition to b formatted..

i am not talking about a separate /home.. because i don't want to keep all my program settings in a fresh installation..

i don't want a dual boot system.i use UBUNTU ONLY..

i'v a 160 Gb hdd

[SIZE="3"]i need to know mount point etc to setup a separate data partition[/SIZE]

can any1 help me?
please..

thank u

---

### Post by Mark Phelps on 2011-04-20
By definition, EVERY partition has to be formatted, at least, initially.  That is how a filesystem is written to an empty space on the media.

Since you want to use Ubuntu only, just format the new partition as Ext4.

If you have all that data in your single partition at the moment, you will need to do the following:
1) Boot from an Ubuntu LiveCD or GParted LiveCD.  Why a CD? Because you will have to shrink the Ubuntu partition, you can only do that if the partition is NOT mounted, and when running from hard drive, the partition must be mounted in order to be used.
2) Shrink the Ubuntu partition to make room.
3) Create a new Ext4 partition.
4) Copy the data to the new partition
5) Access the data on the new partition.
6) Reboot the PC
7) Find the new partition in Places
8) Access the data again
9) Remove the data from the old partition

If you have external media, you can move the data there before you copy it to the new partition.

---

### Post by steninj on 2011-04-20
thank u Mark Phelps,,

right now i have a 15Gb "/" partition&

around 120 Gb "/home"..

is it still possible to do the same?..

or should i do go for a fresh installation?..

otherwise when i create that "ext4" partition as u said,,

what should be the mounting point?
:)

---

### Post by oldfred on 2011-04-20
I had been using Ubuntu for a couple of years with just / (root) and swap with a small shared NTFS partition as part of my dual boot. But when I wanted to convert to 64 bit, I had to do a clean install and created the new /home as recommended. I had new hard drive so I had lots of room and created a new 100GB partition for /home and reinstalled. I quickly realized I wanted the /data partition. The separate /home then only had 1GB used of the 100GB.

How full is your /home? You can shrink it and move data to new data partition if not very full. Otherwise it may be easier to start over.

I mount my /data this way and then link each folder into /home so everything looks normal in /home.

sudo mkdir /mnt/data
sudo chown -R fred:fred /mnt/data
sudo chmod -R 766 /mnt/data
#Edit fstab with your UUID:
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by steninj on 2011-04-20
oh god!!

it seems much complicated than i expected!!

will it be easier to get all these setup if i go for a fresh installation?

---

