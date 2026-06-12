---
title: "changing owner of drive"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by Phil Hansen on 2009-10-28
I have installed a USB external drive and created 2 partitions. 1 x ntfs and 1 x ext3.
The ext3 partition (/dev/sdd2) is owned by root. I want it to be owned by 'phil'
I have searched and found lots of stuff about file permissions but not changing the owner of a drive partition.
Sorry if this has been covered before but I could not find the solution.
Thanks

-------------------
Thanks to all who replied.
Got a better understanding of what is going on and got my permissions back

---

### Post by swerdna on 2009-10-28
If it's mounted in directory "mount_dir" at /path_to/mount_dir, run this command: ```
sudo chown phil:phil /path_to/mount_dir
```and it will change ownership to user=phil, group=phil.

That's for ext3.

NTFS is different, see here for NTFS: [HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu]("http://ubuntu.swerdna.org/ubuntfs.html")

---

### Post by bolucpap on 2009-10-28
By the way, as far as I can tell you will be able to change the owner of the drive when it is inserted into your PC. If you insert into a different PC, that PC will mount the USB as owned by root.

---

### Post by Phil Hansen on 2009-10-28
> **swerdna said:**
> If it's mounted in directory "mount_dir" at /path_to/mount_dir, run this command:
```
sudo chown phil:phil /path_to/mount_dir
```and it will change ownership to user=phil, group=phil 

Sorry missing something.
tried:
```
 sudo chown phil:phil /dev/sdd2
```No change.
Not sure what you mean by /path_to/mount_dir
What should go in there.

---

### Post by ukripper on 2009-10-28
> **Phil Hansen said:**
> Sorry missing something.
tried:
```
 sudo chown phil:phil /dev/sdd2
```No change.
Not sure what you mean by /path_to/mount_dir
What should go in there.

you need to mount your partition first before you can chnage persmissions.

For example: if your drive is mounted on /media/somedrive then you run following command:
```
sudo chown -R phil:phil /media/somedrive
```

replace ***somedrive*** with actual mounted one. if you still cant find it then post output of the following command:
```
sudo mount
```

---

### Post by delphiexile on 2009-10-28
Install this Application:

sudo apt-get install pysdm

Then go to System-> Administration-> Storage Device Manager. Choose your partition (sdb2 as i think) and Click on assistant button , and check after the 5 first checkbox in the mounting tab click after on OK , and now after you remount the partition , you''l be able to write on it.

---

### Post by swerdna on 2009-10-28
> **delphiexile said:**
> Install this Application:

sudo apt-get install pysdm

Then go to System-> Administration-> Storage Device Manager. Choose your partition (sdb2 as i think) and Click on assistant button , and check after the 5 first checkbox in the mounting tab click after on OK , and now after you remount the partition , you''l be able to write on it.
Phil Hansen: be wary of this advice. It does not change ownership IIRC.

And -- regarding this:> **Phil Hansen said:**
> Sorry missing something.
tried:
```
 sudo chown phil:phil /dev/sdd2
```No change.
Not sure what you mean by /path_to/mount_dir
What should go in there.

Follow ukripper's advice to discover the mount directory (or just use the command 'df -Th')

---

