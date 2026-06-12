---
title: "data retrieval from partitions"
date: 2010-02-17
forum: New to Ubuntu
---

### Post by aparolin on 2010-02-17
what does this mean???
typed in:
sudo blkid

result:

/dev/sda1: UUID="aa3ab14b-b95d-4546-b2f3-e797bfe303bd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="510a8b4e-ed53-4dda-9949-8bc89a308dc0" 
/dev/sda6: UUID="a5f8ec65-f213-4a61-96f2-bbca605e6890" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="df1b0e04-5bd7-4657-9694-61242f527dfb" 
/dev/sda8: UUID="25ad1a3a-0d09-425c-a186-5ad23c0a1b13" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="1ae15782-6cb9-4dc2-b0e0-8a132626b05b" 

i believe these are partitions???
could i retrieve data from these partitions??  how??

i have reinstalled 9.04 twice due to problems, but wanted to not loose data files...

am i messed up??

---

### Post by Girya on 2010-02-17
> **aparolin said:**
> what does this mean???
typed in:
sudo blkid

result:

/dev/sda1: UUID="aa3ab14b-b95d-4546-b2f3-e797bfe303bd" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="510a8b4e-ed53-4dda-9949-8bc89a308dc0" 
/dev/sda6: UUID="a5f8ec65-f213-4a61-96f2-bbca605e6890" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="df1b0e04-5bd7-4657-9694-61242f527dfb" 
/dev/sda8: UUID="25ad1a3a-0d09-425c-a186-5ad23c0a1b13" TYPE="ext3" 
/dev/sda9: TYPE="swap" UUID="1ae15782-6cb9-4dc2-b0e0-8a132626b05b" 

i believe these are partitions???
could i retrieve data from these partitions??  how??

i have reinstalled 9.04 twice due to problems, but wanted to not loose data files...

am i messed up??

I'm assuming you've booted with a live CD.
you should be able to mount them and see what is on the partitions.
you need to make a directory :

```
sudo mkdir /mnt/sda1 
```

then mount the file system 

```
sudo mount -t ext /dev/sda1 /mnt/sda1
```

then 
```
ls /mnt/sda1
```

to see what is on the partition

---

### Post by aparolin on 2010-02-17
when i type in that command. i get:  sudo mount -t ext /dev/sda1 /mnt/sda1 mount: unknown filesystem type 'ext'

---

### Post by Girya on 2010-02-17
> **aparolin said:**
> when i type in that command. i get:  sudo mount -t ext /dev/sda1 /mnt/sda1 mount: unknown filesystem type 'ext'

crap typo sorry try 

sudo mount -t ext2 /dev/sda1 /mnt/sda1

---

### Post by aparolin on 2010-02-17
i do have:

/mnt/sda1': File exists

---

### Post by Girya on 2010-02-17
> **aparolin said:**
> i do have:

/mnt/sda1': File exists

what command did you type to get the above?

---

### Post by aparolin on 2010-02-17
typed in this:  sudo mount -t ext2 /dev/sda1 /mnt/sda1 mount: /dev/sda1 already mounted or /mnt/sda1 busy mount: according to mtab, /dev/sda1 is mounted on /media/disk  and this:  ls /mnt/sda1  now search for directory at???

---

### Post by aparolin on 2010-02-17
typed in:


sudo mkdir /mnt/sda1

to get that file

---

### Post by Girya on 2010-02-17
I'm confused 
Did you boot with a live cd?

---

### Post by louieb on 2010-02-17
You should be able to browse from the places menu. May be under the removable media option.

---

### Post by aparolin on 2010-02-17
sorry; forgot to say no



i think sda9 was my last installation;


i am able to boot up, but was trying to retrieve lost data from previous instalation

---

### Post by aparolin on 2010-02-17
should i be looking in my mnt folders for data???

---

### Post by Miljet on 2010-02-17
No, just click on "Places" like louieb suggested. From there you can click on any partition, or all of them, to recover any data.

---

### Post by aparolin on 2010-02-18
must have not worked;

i looked under places and could not find any partitions.



i believe i have identified that the partition exists;  but have not been able to transfer it or identify it on my latest sda.  i think it is sda9.

am i right???

---

### Post by Miljet on 2010-02-18
No, sda9 is a swap partition, as is sda5 and sda7. You only need one swap partition, even if you have more than one installation. I don't know why you have three.

Your data partitions will show up under Places as something like 20.0 GB media or something similar. It will not say partition and it will not be listed as sda1 or sda5 or anything like that.

Please post the result of ```
sudo fdisk -l
```
That is a small L, not a 1.

---

### Post by aparolin on 2010-02-18
Please click one of the Quick Reply icons in the posts above to activate Quick Reply.

---

### Post by aparolin on 2010-02-18
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00006ed5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28998   232926403+  83  Linux
/dev/sda2           28999       30401    11269597+   5  Extended
/dev/sda5           29651       30401     6032376   82  Linux swap / Solaris
/dev/sda6           29325       29628     2441817   83  Linux
/dev/sda7           29629       29650      176683+  82  Linux swap / Solaris
/dev/sda8           28999       29302     2441817   83  Linux
/dev/sda9           29303       29324      176683+  82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by louieb on 2010-02-18
to tell which partition is your install partition use the mount command.
Post the output if not sure. 

```
mount
```

---

### Post by aparolin on 2010-02-18
this looks so screwy:

mount
/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/aparolini/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=aparolini)
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)

---

### Post by aparolin on 2010-02-18
does this make any sense??

---

### Post by louieb on 2010-02-18
> **aparolin said:**
> this looks so screwy:
Actually pretty normal.

This line tells me you have booted to the Ubuntu installed in  partition sda8 
```
/dev/sda8 on / type ext3 (rw,relatime,errors=remount-ro)
```and this is one of your other linux partitions if browse to /media/disk you will see the content of the partition. The  ,uhelper=hal tell me you clicked on that partitions entry in the places menu. 
```
/dev/sda6 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal 
```The rest of the mount command output are various items that Linux mounts  in order to run. 

What is it your looking for? From the looks of things all I see is 3 installs of Ubuntu. If you had data on the drive prior to installing Ubuntu - looks like it is gone now.

---

### Post by aparolin on 2010-02-19
thanx louieb,

im out of tyler...

sofar so good;  alittle history;  my first ubuntu download onto a blank harddrive went perfectly.  i was able to install applications, programs, etc.  and all went well.  perfect operation for months...

then i installed a brandnew ati 4350 video card into the pcie slot (just replaced the weaker video card)...  from there it went downhill...

now the first 2 partitions have ubuntu that turn blank when booting them up;  i feel that my data is still stored in these two iterations and would like to retrieve it into my third partition (sda8)

in other words im trying to retrieve data from the previous ubuntu installations.  

sorry i didnt explain thoroughly before; guess i was too edgy.

if you have other ideas, thanx for ur help
alan

---

### Post by louieb on 2010-02-20
If its there - only 3 choices sda1, sda6 or sda8. Your booting to sda8. 

Ubuntu should be able to browse sda1 and sda6. My guess is your 1st install was in sda1 look in /home/<user name> . 

Might try a  [Puppy Linux]("http://www.puppylinux.com/") live CD. Its partition mounter is pretty good - at least you should be able to tell which partition is witch.

Near Fort Worth here.

---

### Post by aparolin on 2010-02-20
agin thanx.

i was able to boot up sda6, although it was in bad shape (it keeps shutting down ff3 browser among other probs).  went to files and transfered docs, photos, even bookmrks (places.sqlite) to usb sticks.

now plan to install 9.04 with no partitions (clean install).  i have gone to bios and changed video graphics to pcie.  (where new video card is located)

any other suggestions??

appreciate ur help;
again thanx
alan

---

