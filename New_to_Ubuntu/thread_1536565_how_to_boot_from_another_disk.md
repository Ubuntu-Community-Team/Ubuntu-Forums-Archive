---
title: "how to boot from another disk"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by Franz01 on 2010-07-22
I have a ubuntu ruuning (server edition, text only interface)
/dev/sda is my disk

I attached another disk, I mounted it and I extracted all the files from a backup (command used: tar xvpfz backup.tgz -C /)

Now I have this situation (command df):

Filesystem 1k-blocks Used Available Use% Mounted on
/dev/mapper/ubuntu-root   ...                         /   
...
/dev/sda1   ...                                       /boot
/dev/sdb1   ...                                   17% /media/disk

where /media/sdb1 (or /media/disk) is where I extracted all the backup files.

Now what I want to do is to boot from /dev/sdb1 to test the backup/restore procedure...

How can I change the boot? And shall I create another partition for the swap area?
All the disks are virtual, but I suppose it does not make any difference...
Thank you for your suggestion

---

### Post by mapes12 on 2010-07-22
For backup up and restore using tar I do the following:-

> Terminal -
sudo mkdir /HDD2
# creates a folder in the filesystem folder called HDD2

sudo mount /dev/sdb1 /HDD2
# mounts the 2nd HDD Linux partition to the file system via the above directory

Backup /home/mark -
sudo tar cvpzf /HDD2/Backup/Home/Mark/bkp-home-mark.tgz /home/mark

Backup /(root) -
sudo tar cvpzf /HDD2/Filesystem/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media  --exclude=/mnt --exclude=/sys /
# The first two excludes are so that we don't make a second backup of /home and we don't want to backup the second hard drive where we are making the backup to.

On Laptop....................
sudo tar cvpzf /home/mark/Backup/bkp-root.tgz --exclude=/home --exclude=/HDD2 --exclude=/etc/fstab --exclude=/tmp --exclude=/boot --exclude=/proc --exclude=/lost+found --exclude=/media  --exclude=/mnt --exclude=/sys /

SYSTEM DAMAGE!!!!

Reinstall Ubuntu

Then:-

Restore -
Terminal -
sudo mv /HDD2/Backup/Home/bkp-home.tgz /
sudo mv /HDD2/Backup/System/bkp-root.tgz /
# The above will move the tarfiles from the second HDD back into the root file system


sudo su
tar xvpfz bkp-root.tgz -C /
tar xvpfz bkp-home.tgz -C /

Restart the PC.

But there are much easier ways than tar. Post for more info..............

Mark

---

### Post by Franz01 on 2010-07-23
> **mapes12 said:**
> 
But there are much easier ways than tar. 
Mark

For instance... dd command or dedicated tools?

> **mapes12 said:**
> 
Post for more info..............
Mark

My problem is that I need to clone an old linux server from a phisical machine to a vmware. 
The vmware P2V tool requires an agent that we do not have. 

So the idea was to install a new Linux in vmware, create and attach a disk , restore all system and user data to this new disk using tar, and then boot from the second disk. 
Does it make sense?

---

### Post by mapes12 on 2010-07-23
OK. I think I can see what you're trying to accomplish. Here's some more options:-

**1. Use the dd command**

To make an exact copy of a drive install the new drive. Then boot from a Live CD. If the Ubu live CD doesn't work in your machine then try something like Gparted. Accessing the Terminal is the important part. 

Go to Terminal and enter:
```
dd if=/dev/sda of=/dev/sdb
```
#where sda is the old drive and sdb is the new drive. Then disconnect sda from its IDE channel, connect sdb into sda's IDE channell (thus making it sda). And vice versa for sdb. 

To format the old HDD - Boot from a Live CD. Format sdb (the old HDD). Reboot, removing the Live CD and everything will boot from the new HDD.

2. [B]Use an imaging utility like Partimage
[/B]
Backup:

   1. Boot from the Partimage System Rescue CD
   2. Bring up a Terminal which will be a Root Terminal
   3. At the terminal prompt "mkdir /mnt/mydir"
   4. Then mount the second HDD to it "mount /dev/sdb5 /mnt/mydir"
   5. Load Partimage
   6. Select the partition to backup
   7. Tab down to the location line and enter "mnt/mydir/filename" where file name e.g."root140809_partimage.
   8. Note that Partimage saves files with 3 zeros at the end. In the above case the file would be called root140809_partimage.000
   9. Do NOT select any compression

N.B. sdb5 is my HDD configuration. You will need to change this to yours.


Restore:

   1. Boot from the Partimage CD
   2. In Terminal mount the device where the backup is located
   3. On the next screen select the option that places zero's in unused space
   4. Select OK and that's it.

---

