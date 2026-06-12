---
title: "trying to format 2nd drive (ntfs) and failing miserably"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by bigbandwith on 2009-02-13
I installed 8.10 and I love it.  I am ready to put my media my 300g drive so I am trying to reformat to ext3.   It has XP on it now and I can mount it.   When I try gparted it fails.   When I do a terminal session /dev/sd* gives me a permission denied.   Any thoughts.  Since I can mount it, do I even need to reformat?  Thanks.

---

### Post by bodhi.zazen on 2009-02-13
what error message are you getting?

To format the partition you may need to use sudo

try mkfs.ext3

mkfs.ext3 /dev/sdb1

---

### Post by bigbandwith on 2009-02-13
The error is basically a popup that says there was an error perfoming this opperation.  Here is the log that I saved.  This is the error before it starts listing all the sectors.
---------------------------------------------
GParted 0.3.8

Libparted 1.8.9

Create Primary Partition #1 (ext2, 279.46 GiB) on /dev/sdb  00:04:43    ( ERROR )
     	
create empty partition  00:00:00    ( SUCCESS )
     	
path: /dev/sdb1
start: 63
end: 586067264
size: 586067202 (279.46 GiB)
set partitiontype on /dev/sdb1  00:00:00    ( SUCCESS )
     	
new partitiontype: ext2
create new ext2 filesystem  00:04:43    ( ERROR )
     	
mkfs.ext2 -L "" /dev/sdb1
     	
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
18317312 inodes, 73258400 blocks
3662920 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2236 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616

---

### Post by bigbandwith on 2009-02-13
Here is what I got when I tried mkfs.ext3

stevep@Lime:~$ sudo mkfs.ext3 /dev/sdb1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
18317312 inodes, 73258400 blocks
3662920 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
2236 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616

Warning: could not read block 0: Attempt to read block from filesystem resulted in short read
Writing inode tables: done                            
ext2fs_mkdir: Attempt to read block from filesystem resulted in short read while creating root dir
stevep@Lime:~$

---

### Post by bodhi.zazen on 2009-02-13
That is a new one in me :(

See if these links help :

[http://segva.blogspot.com/2007/05/how-not-to-partition-external-hdd-on.html](http://segva.blogspot.com/2007/05/how-not-to-partition-external-hdd-on.html)

[http://ubuntuforums.org/showthread.php?p=6373612](http://ubuntuforums.org/showthread.php?p=6373612)

On that last thread, see post #5 (the last one)

---

### Post by caljohnsmith on 2009-02-13
I would recommend checking the health of your sdb drive just to see if that is possibly the issue. You can do that from Ubuntu by doing the following:
```
sudo apt-get install smartmontools
```
First do the following to save the current health status parameters of your HDD to a file on your desktop:
```
sudo smartctl -a /dev/sdb > ~/Desktop/sdb_health_before_test.txt
```
Then run:
```
sudo smartctl -t long /dev/sdb
```
That command will immediately terminate while the HDD begins its self-test, and it could take quite a while. You can monitor the progress with:
```
sudo smartctl -a /dev/sdb | grep -A 1 -i "self-test execution status"
```
Once the above command says the test is done, then do:
```
sudo smartctl -a /dev/sdb > ~/Desktop/sdb_health_after_test.txt
sudo smartctl -H /dev/sdb
```
And please post the contents of the two files on your desktop so we can see the results.

---

### Post by bodhi.zazen on 2009-02-13
Thank you for helping [caljohnsmith]("http://ubuntuforums.org/member.php?u=530779")

---

### Post by caljohnsmith on 2009-02-13
> **bodhi.zazen said:**
> Thank you for helping [caljohnsmith]("http://ubuntuforums.org/member.php?u=530779")
You're certainly welcome, bodhi.zazen, I just try to help when I can. Hope I wasn't intruding. :)

---

### Post by bodhi.zazen on 2009-02-13
> **caljohnsmith said:**
> You're certainly welcome, bodhi.zazen, I just try to help when I can. Hope I wasn't intruding. :)

You know that you are not intruding, i appreciate both your expertise and your time as a volunteer.

---

### Post by kansasnoob on 2009-02-13
> **bodhi.zazen said:**
> You know that you are not intruding, i appreciate both your expertise and your time as a volunteer.

We need more "intruders" like caljohnsmith!

He knows more than I'll ever be able to forget!

---

### Post by bigbandwith on 2009-02-14
I haven't done the health check up yet, but I did research the articles I was sent previously.
I was able to create a very small partition, so I deleted that.  Then I was able to create a 150g partition.  Then I tried to create another 130g partition and it failed.  I am thinking the sdb' s faulty, so I will do the health checkup and post results.

---

