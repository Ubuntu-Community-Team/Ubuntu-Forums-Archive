---
title: "create mount point"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by supermooshman on 2009-09-05
Hi All,

I just partitioned my second HD with parted.

Now I am looking to make a mount point for this hard drive... but after a day searching for it, I could not find it :confused:


Oh, I looked on google and the forum, but was not able to make any sense out of all this!?
Anyone who can explain this to me in "absolute beginner talk"?

Greatly appreciated!

---

### Post by Xenomorph05 on 2009-09-05
To add a mount point you need to add "/" to it. If you are doing this in Ubuntu select the partition and edit it and then pick the /.

---

### Post by zerhacke on 2009-09-05
Uh, no, if you are adding a second hard drive to your installation you do not want to mount it to /.

---

### Post by coldReactive on 2009-09-05
> **zerhacke said:**
> Uh, no, if you are adding a second hard drive to your installation you do not want to mount it to /.

Then what do you mount it too? /boot?

---

### Post by Xenomorph05 on 2009-09-05
It depends on the purpose of the second partition. It doesn't need a mount point if the first one has Ubuntu and is / already? Unless they want it to be /home?

---

### Post by zerhacke on 2009-09-05
> **Xenomorph05 said:**
> It depends on the purpose of the second partition. It doesn't need a mount point if the first one has Ubuntu and is / already? Unless they want it to be /home?

The OP didn't say he had a new partition, he has a new drive.

Yes, it needs a mount point no matter if Ubuntu is already installed.  Without mounting it how do you propose he uses the disk?

---

### Post by zerhacke on 2009-09-05
> **coldReactive said:**
> Then what do you mount it too? /boot?

Whatever you want that is not already taken. If you mount it to /boot the only files you'll be able to use on that drive are the ones in the /boot directory.  Mounting it to /home is going to make inaccessible your home directories and you obviously don't want that.

I suggest mounting it to /data

---

### Post by Xenomorph05 on 2009-09-05
> **zerhacke said:**
> Without mounting it how do you propose he uses the disk?

I can't say I have tried to mount a 2nd HDD but doesn't Ubuntu auto detect it like any other extra storage device?

---

### Post by yeats on 2009-09-05
Okay, depending on your needs, you can mount /home or /opt or one of the already defined directories for your new drive.  You could also create a new directory to be the mount point:

```
sudo mkdir /mnt/external
```

/mnt is a traditionally-used mount point directory - /media is what Ubuntu uses by default when mounting a CD or USB drive.  But you could create the new directory anywhere you want.

You could then do:

```
sudo mount -t ext3 /dev/sdb1 /mnt/external
```

The -t flag specifies the volume type (could be ntfs or vfat or whatever your volume actually is).  /dev/sdb is likely where your second hard drive is in the /dev directory, so /dev/sdb1 is the first primary partition of that drive.  Does that help?

---

### Post by yeats on 2009-09-05
> I can't say I have tried to mount a 2nd HDD but doesn't Ubuntu auto detect it like any other extra storage device?

Yes - your other option is to locate it in "Places" without using the terminal.  If you want it to automatically mount at boot time, you'll need to add an entry in /etc/fstab.  There are many web sites that explain (in human-readable language) how to do this.

---

### Post by supermooshman on 2009-09-14
hey all,

had some internet problems, I'll have look through the thread and post my findings


Cheers

---

### Post by supermooshman on 2009-11-01
> **chrissharp123 said:**
> Okay, depending on your needs, you can mount /home or /opt or one of the already defined directories for your new drive.  You could also create a new directory to be the mount point:

```
sudo mkdir /mnt/external
```/mnt is a traditionally-used mount point directory - /media is what Ubuntu uses by default when mounting a CD or USB drive.  But you could create the new directory anywhere you want.

You could then do:

```
sudo mount -t ext3 /dev/sdb1 /mnt/external
```The -t flag specifies the volume type (could be ntfs or vfat or whatever your volume actually is).  /dev/sdb is likely where your second hard drive is in the /dev directory, so /dev/sdb1 is the first primary partition of that drive.  Does that help?

He shoots
- he scores


Thanks!

---

