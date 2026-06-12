---
title: "cli question...i think...."
date: 2009-10-24
forum: New to Ubuntu
---

### Post by 1010001er on 2009-10-24
Hi, and thanks for your help.

I'm preparing to migrate from 8.04 to 9.04.

Before I do so, I want to create a separate /home partition, as described here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Once I hit the Apply button, gparted hangs for about an hour, then tells me it can't finish, and offers to save the details in root, which I do.

Next, I try to access save_details.htm, as described at [http://gparted.sourceforge.net/larry/tips/save_details.htm](http://gparted.sourceforge.net/larry/tips/save_details.htm), but I can't. When I open the terminal, it defaults to ubuntu@ubuntu:~$, and I can't figure out how to get to root@GParted:~#, which is making me currently frustrated and potentially imbued with the knowledge that I'm a complete idiot. Please feel free to ridicule me, as I am not a particularly nice person in the first place. :evil:

---

### Post by oldos2er on 2009-10-24
Are you using a gparted livecd, or an Ubuntu livecd?

---

### Post by 1010001er on 2009-10-24
I'm using an Ubuntu live cd.
Was your question also the answer?

---

### Post by sgosnell on 2009-10-24
root@Gparted is the user for a Gparted boot disk.  Ubuntu@ubuntu is the same thing for the live CD.  It should be right where you are.  Those instructions aren't the best I've ever seen.

---

### Post by 1010001er on 2009-10-24
Thank you both very much - the document in question has been retrieved.

Hmmm.

Now what do I do with it? 

Should I open a new thread and post it there? Or would someone care to address it here? Hell, I'll just post it below and see what happens - if no one addresses it, I'll try a new thread. Yeah I'm not used to forums.

GParted 0.4.3

Libparted 1.8.8
Shrink /dev/sda1 from 227.09 GiB to 96.74 GiB  00:50:13    ( ERROR )
     	
calibrate /dev/sda1  00:00:00    ( SUCCESS )
     	
path: /dev/sda1
start: 63
end: 476246924
size: 476246862 (227.09 GiB)
calculate new size and position of /dev/sda1  00:00:00    ( SUCCESS )
     	
requested start: 63
requested end: 202884884
requested size: 202884822 (96.74 GiB)
new start: 63
new end: 202884884
new size: 202884822 (96.74 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:09:35    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

322201 inodes used (1.08%)
6660 non-contiguous files (2.1%)
418 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 14566/617/0
20411516 blocks used (34.29%)
0 bad blocks
1 large file

253087 regular files
37769 directories
132 character device files
26 block device files
68 fifos
496 links
31105 symbolic links (28150 fast symbolic links)
5 sockets
--------
322688 files
e2fsck 1.41.4 (27-Jan-2009)
shrink file system  00:31:22    ( ERROR )
     	
resize2fs /dev/sda1 101442410K
     	
Resizing the filesystem on /dev/sda1 to 25360602 (4k) blocks.
resize2fs 1.41.4 (27-Jan-2009)
resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda1
check file system on /dev/sda1 for errors and (if possible) fix them  00:09:16    ( SUCCESS )
     	
e2fsck -f -y -v /dev/sda1
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

322201 inodes used (1.08%)
6660 non-contiguous files (2.1%)
418 non-contiguous directories (0.1%)
# of inodes with ind/dind/tind blocks: 14566/617/0
20411516 blocks used (34.29%)
0 bad blocks
1 large file

253087 regular files
37769 directories
132 character device files
26 block device files
68 fifos
496 links
31105 symbolic links (28150 fast symbolic links)
5 sockets
--------
322688 files
e2fsck 1.41.4 (27-Jan-2009)
grow file system to fill the partition  00:00:00    ( SUCCESS )
     	
resize2fs /dev/sda1
     	
resize2fs 1.41.4 (27-Jan-2009)
The filesystem is already 59530857 blocks long. Nothing to do!

========================================
Create Primary Partition #1 (ext3, 130.35 GiB) on /dev/sda

========================================

---

### Post by sgosnell on 2009-10-24
I'm not sure what you asked gparted to do, but it looks like it resized sda1 to 96.74GB, then resized it back up to 130GB, the entire disk.

---

