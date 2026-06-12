---
title: "File permissions on new partition"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by irishrm on 2009-04-14
I created a new partition on my hard drive which I can mount.  I can open files from the partition but can not delete or save to it.  The partition is owned by root.  Can someone help please Irishrm.

---

### Post by aktiwers on 2009-04-14
```
sudo chown -R username:username /media/partition/
```

Should do the trick, where username is your ubuntu username and /media/partition is your new partition/mountpoint

---

### Post by irishrm on 2009-04-14
Thanks for that Aktiwers

---

### Post by irishrm on 2009-04-14
I tried the chowm command but I get the reply that a change of ownership is not permitted.  I wonder why?

---

### Post by aktiwers on 2009-04-14
Okay..  Can you give more info on this then?

Post the output of:
```
df -h
```

and the command you used? 
Also what filesystem the partition is and what version of ubuntu you are running

---

### Post by halitech on 2009-04-14
try this
```

sudo chown -R user:user /media/partition
chmod -R 755 /media/partition
```

change user to your user and /media/partition to where the partition is mounted

---

### Post by irishrm on 2009-04-14
Here is the output you requested
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             4.2G  2.5G  1.6G  62% /
varrun                125M  104K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   56K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   39M   86M  32% /lib/modules/2.6.24-23-generic/volatile
/dev/sda2              19G   12G  7.4G  61% /media/sda2
/dev/sda6             4.2G  2.5G  1.6G  62% /media/sda6
/dev/sda7             4.6G  269M  4.3G   6% /media/sda7
sda7 is the partition in question.

---

### Post by halitech on 2009-04-14
do you want to just leave it mounted at /media/sda7 or do you want it mounted in your home folder?

---

### Post by irishrm on 2009-04-14
It would be best mounted at media/sda7 if possible so I can access it with other os.  Sorry I,m a bit slow with the typing

---

### Post by irishrm on 2009-04-14
I tried the suggestion from halitech still getting operation not permitted.

---

### Post by aktiwers on 2009-04-14
Hmm strange..  
What if you run Nautilus as root:
```
gksu nautilus
```

And navigate to the drive and right-click , pick properties and change the permission and owner there?

---

### Post by sofasurfer on 2009-04-14
Or, the method that I use, for lack of knowing the proper way, is to right-click-on-the-directory>properties>permissions>folder-access/file-access.

Permissions (ownership) and file access are two seperate things as far as I know. Even root can not change files if the 'file access' setting is set to 'no access'.

Someone tell me if that is correct? I'm still figuring this stuff out myself.

---

### Post by JohnLM_the_Ghost on 2009-04-14
Hmm... usually partition must be mounted with particular User's ID (UID)
It also a bit depends on what filesystem is the partition (like NTFS, EXT3, FAT32 or others).

So what filesystem is it?

---

### Post by halitech on 2009-04-14
> **irishrm said:**
> It would be best mounted at media/sda7 if possible so I can access it with other os.  Sorry I,m a bit slow with the typing

are you going to be dual booting? if so, where you mount things in linux won't affect windows.


> **irishrm said:**
> I tried the suggestion from halitech still getting operation not permitted.

is the drive mounted currently? Open a terminal and post the output of
```
sudo mount
```

---

### Post by irishrm on 2009-04-14
Tried gksu nautilus. All the options are grayed out so that won't work.  It seems like a difficult problem and I don't want to take up to much of your time trying to fix it. I use puppy as well and I have no problem accessing it with that.  If you have any more suggestions they would be very welcome and thanks for trying.

---

### Post by irishrm on 2009-04-14
I'm slow to keep up.  Its fat32 and is mounted with pysdm

---

### Post by irishrm on 2009-04-14
Sudo mount shows
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sda2 on /media/sda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda6 on /media/sda6 type ext3 (rw)
/dev/sda7 on /media/sda7 type vfat (rw,gid=100)
securityfs on /sys/kernel/security type securityfs (rw)

---

### Post by halitech on 2009-04-14
thats why the commands I gave won't work, they are for linux file systems, not windows as windows doesn't use the same permission system (in fact, it pretty much doesn't use any)

---

### Post by irishrm on 2009-04-14
I formatted sda7 myself for storage mostly. I suppose fat2 was a bad choice. Should I reformat as ext3.  I dual boot windows and xubuntu and I am using puppy on cd.  All a learning curve.

---

### Post by halitech on 2009-04-14
fat32 or ntfs is the best optoins if you want to access it from windows as well unless you want to get the ext3 tool for windows to allow you to read the partition as windows can't read ext3 naticely but linux can read fat32, ntfs formats

---

### Post by aktiwers on 2009-04-14
Is the partition empty now?

Then why not format it from Ubuntu?
```
sudo gparted
```

Find the partition, unmount it and format it. You should be able to use FAT32 fine.

---

### Post by irishrm on 2009-04-14
Thanks for the interest and help everybody.  At least I can open files stored in that partition just can't save from xubuntu and I have learned a bit so how bad.

---

### Post by halitech on 2009-04-14
check out the info here: [http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32](http://www.psychocats.net/ubuntu/mountwindowsfstab#fat32)

---

### Post by irishrm on 2009-04-14
Still catching up. I did the formatting with gparted in xubuntu.

---

