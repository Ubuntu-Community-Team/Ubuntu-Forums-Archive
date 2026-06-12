---
title: "Adding another HDD"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by mirado on 2009-09-30
My computer is running solely on Ubuntu and I would like to add another HDD 
Is there any way to go about doing this without uninstalling and reinstalling?

---

### Post by Crafty Kisses on 2009-09-30
Yes it's possible to put a new drive in without reinstalling Ubuntu. ;-).  First you're going to have to put the new drive in, then you need to format it with Gparted or cfdisk, doesn't really matter, I would suggest GParted it's more user friendly, so in a terminal run:
```
apt-get install gparted
```
Then, run gparted then you need to format the drive to ext3 or whatever you would like doesn't really matter, some prefer LVM others ReiserFS. You can also run as root:
```
mkfs -t ext3 /dev/sdb2
```
That will format the drive in ext3. Anyway, once you have formatted the drive you then need to make a mount point you can do this by running:
```
sudo mkdir /media/drivename
```
So for example you can make the mount point, let's just say for now "foo" then you can run:
```
sudo mkdir /media/foo
```
You then need to edit your filesystem table or as it's called "fstab" so run in a terminal as root:
```
gedit /etc/fstab
```
Then you need to add:
```
/dev/sdb1    /media/foo  ext3    defaults     0        2
```
Remember that is assuming you have formatted the drive using ext3 and the mount point is called foo. Then you can run:
```
chmod +t /media/foo
```
Then you can mount the drive in the terminal by running:
```
mount /media/foo
```
Then if you want to unmount the drive, you would just simply run:
```
umount /media/foo
```
If you have any problems, let me know and I'll be glad to help you more.

---

### Post by mirado on 2009-09-30
Good God
I love this forum!
I'll post how it goes

---

### Post by mirado on 2009-09-30
terminal says:
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
mkfs.ext3: Permission denied while trying to determine filesystem size

---

### Post by mirado on 2009-09-30
I ran this line prior to following your steps to see logical name of the drive (I am trying to run 2 parallel drives) 
sudo lshw -C disk

[FONT=Verdana]The output told me the logical name was [/FONT]"/dev/sdb"
[FONT=Verdana]The filesystem table on the other hand is telling me this drive being recognized as "/dev/sda5" and is in "swap" format

I would imagine that having the proper logical name for the drive is imperative...
Which would be the best one to choose?:confused:

Sorry, I am a very virgin user
Please be patient with me[/FONT]

---

### Post by nhasian on 2009-09-30
you should just create the partition with gparted.  System->Administration->partition editor.  if you dont have that menu entry you can install gparted with:

```
sudo apt-get install gparted
```

If your running 9.04 doesnt gparted allow you to create an EXT4 partition?  That is preferred and is the default filesystem in Karmic.

then I would do:
```

sudo blkid
```
to get the new partition's UUID and add it to /etc/fstab.

on my system i created a directory /data and that is where I mount my secondary hard disk.

---

### Post by mirado on 2009-09-30
The HDD I'm using right now is in EXT3 (I do plan on using them side by side)
Would this make rise to some problems or is it nothing to worry about?

---

### Post by mirado on 2009-09-30
Much appreciated, guys
Quick fix even for a mentally handicapped citizen as myself\\:D/

---

### Post by tedrogers on 2009-12-04
I've just done this with an external drive, as the automount was giving me a cacky mount point (/media/f433k-3rerw-trrre...blah blah etc).

Needless to say your tutorial worked fine (so thanks for that Crafty Kisses!), but I have to mount as root or sudo it.

Is there any way I can mount as a regular user?

Also my automount fails now, and reports that I need to be root to mount. :(

Is it a simple fstab thing?

Thanks.

---

### Post by tedrogers on 2009-12-04
It's okay, I sorted it.

I just replaced DEFAULT in the fstab entry with these options:

rw,exec,auto,user,sync

Seems to be working fine now.

Do you know if I really need to have suid and dev in the option list too...and should I use async or sync with a USB hard drive?

---

### Post by tedrogers on 2009-12-05
Oh no! Horror or horrors.

For some reason, the drive was working fine, then I removed it, connected an SD card, which assumed the same drive number (/dev/sdb1). I thought nothing of it at the time, but when I connected the drive back again all my partitions were gone!

Using testdisk I was able to recover one of the two partitions on the drive, and rebuild the partitions table, but the other partition remains inaccessible.

How could this have happened?

---

### Post by brianmch on 2010-04-22
Thanks for the instructions in this thread, very helpful.  I wanted to add one thing.  I rebooted after adding a new disk (space for recordings in mythtv).  The machine hung with a message "verifying DMI pool".   It was trying to boot from the newly added disk which has no OS on it and no MBR, so I had go into the BIOS and change the boot order.  

Took me a little while to figure it out, so I thought I would add a note here to help some other newbie.

Regards,
Brian

---

