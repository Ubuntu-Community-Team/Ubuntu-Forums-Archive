---
title: "More hard disk space"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by Leshinsky on 2009-06-07
Ok i installed ubuntu using wubi... I choose the full 15 gigs that it would let me use (giving windows 205 gigs as i got a 220 gig hard disk. ) i dont use windows anymore, but only have like 200 mb left on ubuntu.... i would like to apply more of the 205 gigs free from the windows side to ubuntu, just to store files.  how can i do this...

---

### Post by nandemonai on 2009-06-07
As far as I know it's pretty tricky to resize a wubi install. Personally I'd recommend backing up and doing a proper install.

That said:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)

---

### Post by TheMendez1 on 2009-06-07
If your not going to use windows any more you can format your windows partition then I guess apply 
it to your Ubuntu one. but then again I'm not sure if you can do that. I think your better of buying a new hard disk and reinstalling ubuntu on there, just because its alot simpler alot faster and there is a lot less room for error.

---

### Post by nandemonai on 2009-06-07
> **TheMendez1 said:**
> If your not going to use windows any more you can format your windows partition then I guess apply 
it to your Ubuntu one. but then again I'm not sure if you can do that. I think your better of buying a new hard disk and reinstalling ubuntu on there, just because its alot simpler alot faster and there is a lot less room for error.

Wubi installs into a virtual disk on the windows partition. Formatting Windows will in turn format Ubuntu as well.

---

### Post by Leshinsky on 2009-06-07
I used these commands 

cd /host/ubuntu/disks
sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
sudo mkfs.ext3 -F extra.disk

Got this in terminal.

matthew@ubuntu:~$ sudo sh wubi-add-virtual-disk /home 15000
[sudo] password for matthew: 
sh: Can't open wubi-add-virtual-disk
matthew@ubuntu:~$ cd /host/ubuntu/disks
matthew@ubuntu:/host/ubuntu/disks$ sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000
1+0 records in
1+0 records out
1000000 bytes (1.0 MB) copied, 0.60391 s, 1.7 MB/s
matthew@ubuntu:/host/ubuntu/disks$ sudo mkfs.ext3 -F extra.disk
mke2fs 1.41.4 (27-Jan-2009)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
610800 inodes, 2441650 blocks
122082 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=2503999488
75 block groups
32768 blocks per group, 32768 fragments per group
8144 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 35 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
matthew@ubuntu:/host/ubuntu/disks$ 

After following this.

Open a terminal (Applications -> Accessories -> Teminal), and enter these commands (this will create a 10 GB extra.virtual.disk, adjust line 2 to change these): 

cd /host/ubuntu/disks sudo dd if=/dev/zero of=extra.disk bs=1MB count=1 seek=10000 sudo mkfs.ext3 -F extra.disk

So where would the extra space be or what did i mess up.

---

### Post by presence1960 on 2009-06-07
If you don't use windows anymore back up your data to a usb drive or worst case to CDs/DVDs. Pop in the Ubuntu live CD and boot from it. When you get to the partitioner screen Prepare disk space choose "use Entire Disk". It will do just that with Ubuntu on it. Bye, Bye Windows. After install you can transfer your data back to Ubuntu.

**_No need to buy a new hard disk unless you need one._**

---

### Post by Leshinsky on 2009-06-07
Where do i get that program so that i can do that.... i have to much to it all on a thumb drive. so tomorrow i am getting a shell for a old internal drive.... where i will back all my information to... but i dont know where to get the full version of ubuntu.

---

### Post by presence1960 on 2009-06-07
what program? The Ubuntu Live CD? That is the disk you used to install Ubuntu. If you don't have it get it here: [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)
Download the iso file and burn it as an image to a CD-R at the slowest speed possible. If not sure how do this : [https://help.ubuntu.com/9.04/switching/installing-burning.html](https://help.ubuntu.com/9.04/switching/installing-burning.html)

---

### Post by Leshinsky on 2009-06-07
i dont have a cd burner so any ideas

---

### Post by nandemonai on 2009-06-08
> **Leshinsky said:**
> i dont have a cd burner so any ideas

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Leshinsky on 2009-06-08
Ok, so im trying to create a bootable usb flash drive... when i go to the program to make one i get a error message that my computer cant read the path or something like that.  any ideas.  or how do you do it.. i downloaded ubuntu-9.04-desktop-i386.iso to my deaktop and unpacked it.  what am i doing wrong.  i read the above directions abd im so lost...

---

### Post by Leshinsky on 2009-06-08
ok, so i put the ubuntu install onto my flash drive... formatted my hd, and now when i click on the flash drive it says wubi.exe.. is this ubuntu install (full or wubi install.) when i click on it it tells me to restart the comptuer and leave the cd in the drive.... i cant make this bootable... i need help bad. ......i tried doing the prev posts but was so totally lost.... i need help.

---

