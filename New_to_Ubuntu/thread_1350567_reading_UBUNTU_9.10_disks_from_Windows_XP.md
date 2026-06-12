---
title: "reading UBUNTU 9.10 disks from Windows XP"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by thegreeneyes on 2009-12-09
Hi, I work most of the time on Ubuntu, but sometimes I need to boot in Windows XP. For previous versions of Ubuntu I could read the linux disks using Ext2IFS_1_11a.exe or Ext2Fsd-0.48, but with version 9.10 I cannot. Are you aware of any way to read Ubuntu's disks from Windows?

Thanks

thegreeneyes

---

### Post by Chesamo on 2009-12-09
[s]Depends on what filesystem you are using. ext3 is still supported by a few tools, but ext4 support isn't available.[/s]
I take that back. The latest ext2fsd appears to work... are you sure you don't have a configuration problem?

[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by louieb on 2009-12-09
The probable reason you can't read ext3 file-systems from windows is Inode size.

Both the readers Ext2IFS_1_11a.exe or Ext2Fsd-0.48, work with Inode size of 128. Newer versions of Ubuntu  build ext3 file-systems with Inode size 256. 

```
sudo tune2fs -l /dev/sda1 | grep -i Inode 
```

have not done it but IIRC tune2fs can change the Inode size. Don't know if it is worth it either.

---

### Post by thegreeneyes on 2009-12-09
Thanks for your comments, I tried again to install ext2fsd but the only thing I get after installation is the contents of the / folder, but only the names of the folders inside / , and inside each of the shown folders (bin, etc, mnt, home ... ) there is nothing.

Unfortunately I did not use the -O switch when partitioning the disks, no I imagine it is too late, unless I reinstall Ubuntu again from scratch, isn it?

I came back to Ubuntu and verified that Inode is set to 256. If I change it to 128, will the content of my Ubuntu disk be affected? (will I lose every files already in the disk?)

Thanks

Victor

---

### Post by thegreeneyes on 2009-12-21
Finally the only solution I found is :  

1) resize the Ubuntu Partition in ext4 format, using gparted, to free enough space to store the files I might need from Windows.

2) create another partition in the available space using ext2 where I copied the files I needed in both systems

3) I linked the new partition to my home folder so I can access it straightforward.

I hope this helps if anyone is wondering about how to proceed.

---

