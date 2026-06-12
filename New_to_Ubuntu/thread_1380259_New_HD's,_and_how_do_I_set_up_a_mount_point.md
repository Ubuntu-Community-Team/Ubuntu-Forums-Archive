---
title: "New HD's, and how do I set up a mount point?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by GeordieJedi on 2010-01-13
Hi all, hope your all well.

Ok Ive just got myself a nice shiny new 1 TB internal sata HD.
Now Ive just repartitioned it up with patred magic and setup roughly,
5 x 200GB partitions (in ext3 format).

Now I want Ubuntu to auto-mount these partitions (as they're gonna be
my main data partitions.

(I've been told that I would be wise to add the required changes to
the fstab file, and add the mount points to the mnt dir.

So how do I set up a mount point?



Thanks in advance for any help.

---

### Post by halitech on 2010-01-13
I know the info here is old but it should still work

[http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3](http://ubuntuforums.org/showthread.php?t=174562&highlight=mount+ext3)

---

### Post by fancypiper on 2010-01-13
Create the mount point with the **mdkir** command.

Examples:
sudo mkdir /mnt/storage
mkdir /home/data
sudo mkdir /pub

---

### Post by bodhi.zazen on 2010-01-13
> **fancypiper said:**
> Create the mount point with the **mdkir** command.

Examples:
mkdir /mnt/storage
mkdir /home/data
mkdir /pub

You will need to use sudo mkdir for /mnt/storage and /pub

You can use mkdir, without sudo, for anything in your home directory.

---

### Post by oldfred on 2010-01-13
More info here:

Beginning you have already done:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

---

### Post by oldfred on 2010-01-13
I think I followed instructions here to mount my /data.

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

With my data in /usr/local I do not see it in the file browser which I prefer. I deleted all my folders in /home and mounted them from the /usr/local/fred/data like this:

ln -s /usr/local/fred/data/Music

One of the comments in the above line has a one line bash command to mount all of them but I could not get it to work, so I just copied & edited my lines for all my folders. (  I think she had an extra ; somewhere)

---

### Post by GeordieJedi on 2010-01-18
WooHoo! I seem to be getting somewhere now. :-D

Ok, I've managed to add a mount point, add the necessary line in fstab
and It auto mounts.

Now, if I choose the properties dialogue of the partition itself (from the
desktop) it says =
"The permissions of "Music_01" could not be determined.

(N.B. It also says this on my external drive, but I suspect that it's due to
the fact that it's NTFS formatted. And I haven't had any permissions
problems at all on the external drive).

When I select properties on the individual files, they are owned by myself,
I can add/delete files on the new hd partition.

So my next question is am I ok to now move/copy all of my Music
collection from my external drive to my new drive?

Thanks once again for all the help.

---

