---
title: "Change disk in Linux"
date: 2011-08-01
forum: New to Ubuntu
---

### Post by nicos99 on 2011-08-01
Hello all,
I have a linux system which contains 2 harddisk, disk2 is most servered to Database, now, since the DB is growing, we have to change disk2 to another disk which has more capacity.
Last time, I used dd to move out all data on disk2 and move back in to a new disk, it's a nightmare, never finished. Of course, as I'm quite new for linux, so I would like you guys, in this situation, what method will be better to change the new disk, and if this new disk needs to make the partition first?
Thanks in advance.
Nicos

---

### Post by Paqman on 2011-08-01
Plug the new disk in and boot up. You'll need to format the drive (the normal filesystem is Ext4, although there are others). If you're running a graphical desktop use Disk Utility. If this is a server that doesn't have a GUI you'll need to make sure of the location of the drive:
```
sudo fdisk -l
```
then format it
```
sudo mkfs.ext4 /dev/sdaX
```
...where X is the number of the drive that you want to format. Be very careful! Make sure you have the right one!

You'll need to create a mount point for the new drive:
```
sudo mkdir /new/mount/point
```
Then add that mount point to fstab:
```
sudo nano /etc/fstab
```
Just copy and paste the entry for your existing drive, but change the mount point to the one you just created. Save the changes and run:
```
sudo mount -a
```
If it doesn't spit out any errors then you're good to go.

Then just copy your data over using the file manager (for GUI) or the cp or mv command (non-GUI). 

The problem with dd is that it copies free space as well as data. If your drive isn't particularly full that wastes a lot of time.

---

### Post by nicos99 on 2011-08-02
Thank you very much, paqman. I'm very appreciate for your answer. But I still have a question, why you format the disk with ext4, my original disk is ext3. And I have another question, for example, I have this server with an acronis image, if I just change the disk, and I recover the image on this disk, what will happened?
 
I did on a test server, if I fdisk -l, I can see the real capacity of new disk, like 146G, but I use df -h, it seems only show the old disk capacity?
 
Thanks

---

### Post by Wim Sturkenboom on 2011-08-02
The image might contain the old partition table of the original disk; so when you put the image on the disk, you also put the old partition table back. I've never dealt with this, so can't say if you can resize (which is basically what you want, I guess).

---

### Post by nicos99 on 2011-08-02
Exactly, I'm not sure I can resize with this old partition on the new disk?

---

