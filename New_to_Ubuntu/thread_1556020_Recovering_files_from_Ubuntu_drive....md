---
title: "Recovering files from Ubuntu drive..."
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Zeptinune on 2010-08-18
So my Unbuntu install died 5 hours after installing it. I am left with a dead drive that gives me the error:
*'No system part specified, please remove the part and press any key'*
 
This is, however something that does not bother me.
What does bother me is what is on the drive before it died. I had 2 partitions. The second which I need to get files from.
 
At the moment I still have my SD Card that I can use to either boot into Ubuntu *from the SD* or re/install over the HDD (which would even further screw my chances of getting my stuff back).
 
So basically I need a way to get my stuff off the Partition. Does anyone know the best way I can go about doing this.
 
The only option I can see avaliable to me is installing XP ONTO a USB drive and then using that to run a recovery program which will post the recovered files to an external drive. But other people have told me that genuine ways exist using Ubuntu to recover my files.
 
Does anyone have any suggestions?

---

### Post by ubudog on 2010-08-18
Boot the live cd and mount the partiton.  You can create another partition and put them on that, copying them back over once you get your new Ubuntu installation or whatever you do.

---

### Post by Zeptinune on 2010-08-18
Hey thanks for your reply. I am not entirely sure what you mean however.. I want to recover as many files as I can from my Disk.
 
So you are advising me to boot into Ubuntu from my SD Card and then create a partition?
Out of my damaged HDD that I want to get my files from?
(I don't want to format it because it further reduces the chances of me getting anything off the disk) and then what do I do after that?
 
Is there a program on Ubuntu that could get my files back? Or do I have to do a windows install...?
 
Please be a little more specific sorry :(

---

### Post by ubudog on 2010-08-18
Ok.  Sorry I wasn't more specific.  First of all, start into the live cd interface.  Then, mount your damaged Ubuntu partition, using the command:
```
sudo mount /dev/nameofpartition /mnt
```
(nameofpartion, being, well, the name of your partition)

Then, if you have a usb flash drive that is big enough, insert it, it will automount.  Then, copy the files you want from the damaged partition to the flash drive.  Say you want to copy your home directory from the damaged partition to the flash drive, this would be the command:
```
sudo cp -a /mnt/home/nameofhomedir /media/nameofflashdrive
```
(assuming you already mounted your damaged partition on /mnt)

That would work for the flash drive.  If there is not enough space on the flash drive, you can make another partition using Gparted (be careful with this tool) and copy the files to it, copying them back to your working OS when you are done.  To copy the files from the damaged partition to the new partition, first you have to mount the new partition:
```
sudo mount /dev/nameofnewpart /mnt
```
Then, to copy the files from the damaged part. to the new part., this would be the command:
```
sudo cp -a /mnt/damagedpart/home/nameofuser /mnt/newpart/
```
If you are going to copy the files on the new partition to a Windows computer, make sure you make it a fat32 partition when you use Gparted, so you are able to mount it in Windows.

Hope that's a tad bit more specific.  Lol that was a long post.

---

### Post by ubudog on 2010-08-18
Hope that works for you, good luck.  And let me know if you have any questions BEFORE you format the new partition.

---

### Post by oldfred on 2010-08-18
Testdisk will often repair a damaged partition. It also has photorec which recovers files (not just photos) but since it does not have names if is just a recovery of what it thinks look like complete files.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)

---

### Post by ubudog on 2010-08-19
That too.

---

