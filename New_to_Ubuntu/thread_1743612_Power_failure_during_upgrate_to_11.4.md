---
title: "Power failure during upgrate to 11.4"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by D_2 on 2011-04-29
I was trying to upgrade my server from 10.10 to 11.4 when in the middle of the upgrading my power went out and now the system is having problems mounting the HDD.
 
What I am wondering is, is there any way to get to the WWW directory on the server and then back that up onto a USB drive, this is the only directory I need files from and then from there I can then repartition the entire thing and do a fresh install of 11.4 but I don't want to do that untill I can get the WWW directory backed up. How is the best way to do that.
 
Thank you to any and all that can help

---

### Post by fabricator4 on 2011-04-29
> **D_2 said:**
>  directory I need files from and then from there I can then repartition the entire thing and do a fresh install of 11.4 but I don't want to do that untill I can get the WWW directory backed up. How is the best way to do that.


Boot up almost any LiveCD distro, mount the partition and copy the files off it to your nominated backup device.

If the partition is totally scrambled or corrupted you'll have to send a bit more time recovering it, but hopefully it won't come to that.

Chris.

---

### Post by K_45 on 2011-04-29
Try a Live CD and then mount with

```
sudo mount /dev/sdaX
``` substituting X with the home partition number

If that doesn't work and its unmounted run a file system check first

```
sudo fsck -y dev/sdaX
```

---

### Post by D_2 on 2011-04-29
Thank you for your replaies, I have a couple of questiions. (I am glad this place has a beginner talk area) how do I find out the partition number I need, also what are the steps I need to enter to transfer the WWW directory to a USB thumb drive. I know I can spend some extra time looking the answers to these questions, but if some one can post them here it will save me some extra time and I know it will be more accorate then what I might find else where on the internet.

---

### Post by K_45 on 2011-04-29
Find out with:

```
sudo fdisk -l
```

and copy them normally as you would

---

### Post by Zill on 2011-04-29
> **D_2 said:**
> I was trying to upgrade my server from 10.10 to 11.4 when in the middle of the upgrading my power went out and now the system is having problems mounting the HDD.
 
What I am wondering is, is there any way to get to the WWW directory on the server and then back that up onto a USB drive, this is the only directory I need files from ...
Not much help to you unfortunately but to anyone else reading this thread my advice is to *always* have good backups of *all* your essential data *before* upgrading.

Things can (and do!) go wrong so always prepare for the worst but hope for the best. ;-)

---

### Post by D_2 on 2011-04-30
I booted up the computer using a live CD and when it gets to the desktop I can't access any menu because all I get is black boxes so I pulled the drive and booted on a laptop using the same live CD and the server's drive connected to the laptop using a USB 2.0 drive adapter and the live CD sees it as dev/sdb1 but when I run the command ```
sudo fsck -y dev/sdb1
``` I get back is fsck from util-linux-ng 2.17.2 then the prompt is back, if I try the command```
 sudo mount dev/sdb1
``` I get back mount: can't find dev/sdb1 in /etc/fstab or /etc/mtab if I run the command ```
sudo fdisk -l
``` I get back disk /dev/sdb: 500.1GB and /dev/sdb1 and under system it says Linus LVM I also have dev/sdb2 system extended and dev/sdb5 system linux

So what do I need to do to get this drive repaired, so I can copy the files onto another device, if I can do it onto my laptop good, they are just files that are in the WWW directory, or at least I can start doing something.

I did try to click on the drive using the live CD under computer and noticed that there is a green VG on the icon of the drive, and when I click on it I get a message that says failed activation drive: Error starting job: Failed to execute child process "vgchange" (No such file or directory) In the computer group that shows the other drives and partitions on the drives connected to my laptop I do have an icon that says 500GB 225MB Filesystem and I think it is showing me the extended partition but I am not sure.

---

### Post by D_2 on 2011-04-30
If connecting the server drive to my laptop to see if the live CD can repair it, what other options can I do with the info I posted in the post above.

---

### Post by fabricator4 on 2011-04-30
> **D_2 said:**
> If connecting the server drive to my laptop to see if the live CD can repair it, what other options can I do with the info I posted in the post above.

The commands given, unfortunately were incorrect.  Only slightly though...

```

sudo fsck -y /dev/sdb1

```

Will check the drive.

```

sudo mkdir /media/temp
sudo mount /dev/sdb /media/temp

```

Will mount the drive so you can access it as /media/temp.  Your home directory on this scheme will be /media/temp/home/username

Chris

---

### Post by D_2 on 2011-04-30
Using the command```
 fsck -y /dev/sdb1
``` I get back
fsck from util-linux-ng 2.17.2
fsck: fsck.LVM2_member: not found
fsck: Error 2 while executing fsck.LVM2_member for /dev/sdb1

what needs to be done now

---

### Post by fabricator4 on 2011-04-30
> **D_2 said:**
> 
fsck from util-linux-ng 2.17.2
fsck: fsck.LVM2_member: not found
fsck: Error 2 while executing fsck.LVM2_member for /dev/sdb1

what needs to be done now

Yikes, it looks like the LV is scrambled.  This is uncharted territory for me, anything I suggest wrt directly operating on the LV (logical volume) is just as likely to make things worse.

I think I would install testdisk and use that to analyse the partition: maybe it can suggest an effective repair.

Apart from that, see if anyone else can help you.  If you don't get any more replies here, start another thread with this more specific information in the Title.

Chris

---

