---
title: "help with drive space.."
date: 2011-05-27
forum: New to Ubuntu
---

### Post by spillage2 on 2011-05-27
I soo need help.

I have two 650gb drives.

One has my / and swap area..the other has my /home folder and a folder called all.

My /home folder is showing as 15gb and the all folder is 42.7gb.

Free space is only 82gb..

This is what I get from df -h..

/dev/sdb1             587G  468G   90G  84% /home


I'm lost as to where all this extra space has gone...gparted shows the same results..

Cleared out my trash and its getting very light outside so I give up..

If anyone has any ideas please let me know..

Spill.

---

### Post by LowSky on 2011-05-27
OK? UM.... How did you install Ubuntu?

What are the sizes of each partition?

---

### Post by quarkhirad on 2011-05-27
> **spillage2 said:**
> I soo need help.

I have two 650gb drives.

One has my / and swap area..the other has my /home folder and a folder called all.

My /home folder is showing as 15gb and the all folder is 42.7gb.

Free space is only 82gb..

This is what I get from df -h..

/dev/sdb1             587G  468G   90G  84% /home


I'm lost as to where all this extra space has gone...gparted shows the same results..

Cleared out my trash and its getting very light outside so I give up..

If anyone has any ideas please let me know..

Spill.


Open  terminal and  type the following. Please  paste  the outputs  of all the commands.

```
khirad@jeena:~$ cat /etc/fstab
khirad@jeena:~$ mount
khirad@jeena:~$ df -h

```
 
Please note in your terminal khirad will  be  your username and jeena  will be  your hostname.

Also please open  gparted  and take  a screen  shot of gparted for both your HDD and post the picture.

---

### Post by spillage2 on 2011-05-27
```
 mark@mark-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=3ec59121-6915-4b6d-8c07-f252e5a87a7e /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=51c11252-d0fe-4b15-9590-947b781b655f /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=11e85568-fbf6-4671-95af-240a718dd347 none            swap    sw              0       0
mark@mark-desktop:~$ 
   
``````
 /dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mark/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mark)

```and 

```
 Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             578G  197G  352G  36% /
none                  2.0G  316K  2.0G   1% /dev
none                  2.0G  100K  2.0G   1% /dev/shm
none                  2.0G   84K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda1             587G  468G   90G  84% /home

```I had issues with the sata drives being picked up so after removing the cable and re connecting got them to work.

I was up till 5 this morning messing around with this.. Maybe a complete install now I have had some sleep might be wise..

After some digging around this morning after a bit of sleep I have noticed that if I move data from my second drive (containing /home) gparted does not register that free space...in case this helps..

cheers 

spill.

---

### Post by grahammechanical on 2011-05-27
I do not know what I am talking about. Please remember that. But I do notice this:

> / was on /dev/sda1 during installation

Compare that to this:

> /dev/sdb1   .... mounted on /

And, 

> /home was on /dev/sdb1 during installation

with

> /dev/sda1 ... mounted on /home

When I run those commands on my system, then I find that my / partition and my /home partition are listed as being on sda1 and sda3 during installation (I only have one drive) and they are still listed as being mounted on the same place by the df -h command.

Something is messed up on your system.

Regards.

---

### Post by spillage2 on 2011-05-27
thanks grahammechanical for the input.

I am running two separate hard drives and had to swap the sata leads around..although I cannot understand why my second disc that holds my /home folder will not register a reduced size if something is deleted from it..and there was me thinking a separate /home drive is the way to go...


much much much to learn...

---

### Post by coffeecat on 2011-05-27
df /h shows that you have only 90G available of your 587G home partition. Have you ever used a root nautilus to delete things in your home partition? If you use a root nautilus to delete things in /home when you don't have a separate home partition, then the "deleted" files are not deleted at all, merely moved to root's trash which is in the /root folder in the root (/) partition. I'm not sure what happens with a separate home partition but if you ever did delete stuff with a root nautilus then my guess is that it is still sitting in a hidden folder somewhere in your home partition.

---

### Post by spillage2 on 2011-05-27
@coffeecat...No I too thought this so ran sudo nautilus through terminal and cleared it through but not much there...

Think its time to have another go at a fresh install and see if it makes any difference..

At least I'm getting to use terminal commands more...;)...

---

### Post by coffeecat on 2011-05-27
> **spillage2 said:**
> @coffeecat...No I too thought this so ran sudo nautilus through terminal and cleared it through but not much there...

Think its time to have another go at a fresh install and see if it makes any difference..

Oh, wow. No need to do a re-install. :| Or, at least, before you do, open a home folder, press ctrl-H to view hidden files/folders and see if there are any called Trash-01.

---

### Post by spillage2 on 2011-05-27
there were about 3 .Trash folder in there and all have been removed although they were not showing as that large..

I wonder if it was due to /home being on the second drive as it only shows the one file system and not two separate drives..

I could see that if all data from both was on one drive then i might be close to being full..

---

### Post by coffeecat on 2011-05-27
Your home being on a separate HD would make no difference. We haven't been able to explain where that space has disappeared to.

---

### Post by spillage2 on 2011-05-27
this was a fresh install and all the second drive had on it was one folder with some download on and a copy of my old /home folder.

I have not idea how I could be increasing the usage by adding a folder but If I deleted it the size would not decrease...

I tried this by being the user and using gui, using nautilus as sudo and doing both using the terminal...

I am going to take the drive back to how it was and try another fresh install and make sure no mistakes were made late last night..

---

### Post by quarkhirad on 2011-05-28
Spillage2

Please type the following in terminal  

Sudo fdisk -l 

Then paste the  output   here.

So that we can see how the disk has  be partitioned.

---

