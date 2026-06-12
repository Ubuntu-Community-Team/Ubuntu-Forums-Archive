---
title: "Bunch o' Failed Installs"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by mlnease on 2009-04-10
Hello,

Had a bad crash this week and attempted a number of reinstalls before I finally got one to work properly.  Because of this I see quite a list of--what--extra partitions?  Or...

If someone could advise me as to how to display this I'll copy and paste it here then take it from there.

Thanks in advance.

mike

---

### Post by Elfy on 2009-04-10
```
sudo fdisk -l
```

will list your partitions

```
df -h
```
will tell you which of them are mounted

---

### Post by mlnease on 2009-04-10
> **forestpixie said:**
> ```
sudo fdisk -l
```

will list your partitions

```
df -h
```
will tell you which of them are mounted

Thanks for the quick response!

sudo fdisk -l
Disk /dev/sda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58514e3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2243    18016866   83  Linux
/dev/sda2            2244        4870    21101377+   5  Extended
/dev/sda5            4687        4870     1477948+  82  Linux swap / Solaris
/dev/sda6            2244        4578    18755824+  83  Linux
/dev/sda7            4579        4686      867478+  82  Linux swap / Solaris

Partition table entries are not in disk order

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              18G  2.9G   14G  18% /
varrun                248M  112K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
udev                  248M   60K  248M   1% /dev
devshm                248M   40K  248M   1% /dev/shm
lrm                   248M   39M  209M  16% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       18G  2.9G   14G  18% /home/mn/.gvfs

Pardon my ignorance but these data mean little too me.  Do they suggest to you any course of action you might advise, or should I just leave it all alone?

Thanks Again,

mike

---

### Post by Therion on 2009-04-10
> **mlnease said:**
> Pardon my ignorance but these data mean little too me.  Do they suggest to you any course of action you might advise, or should I just leave it all alone?
Well you do have an extra partition or two there, that's for sure.  What to do next depends on what you want ultimately.  Do you just want a standard, clean install; with Ubuntu being your sole OS, do you want to dual boot, or what?

---

### Post by Elfy on 2009-04-10
Depends what you want to do, at the moment you have 1 partition not being used - sda1 and 2 swap partitions - it's likely that you only need 1 of them.

You can check what is actually on sda1 by mounting it in nautilus. I assume it is the original install unless you overwrote it at some point.

You could for instance lose sda7 and resize sda6 to include it and leave sda1 as a seperate partition and add it to fsatb as a data partition.

What do you want to do?

---

### Post by mlnease on 2009-04-10
> **forestpixie said:**
> Depends what you want to do, at the moment you have 1 partition not being used - sda1 and 2 swap partitions - it's likely that you only need 1 of them.

You can check what is actually on sda1 by mounting it in nautilus. I assume it is the original install unless you overwrote it at some point.

You could for instance lose sda7 and resize sda6 to include it and leave sda1 as a seperate partition and add it to fsatb as a data partition.

What do you want to do?

Good questions, both:  Therion got it right, I want a standard, clean install; with Ubuntu being my sole OS.  Should I assume this would entail forestpixie's suggestion to lose sda7 and resize sda6 to include it and leave sda1 as a separate partition and add it to fsatb as a data partition?  I'm somewhat afraid to increase the size  of sda6 though, as I think that reducing it was what made the last install work.  Also I think I like the idea of leaving sda1 as a separate partition and adding it to fsatb as a data partition--but this is all well over my head so I'm not certain.  Maybe best to keep it simple.

Thanks again to you both for your patience.

mike

---

### Post by Therion on 2009-04-10
Maybe it's time to reformat and do a fresh install?

---

### Post by Elfy on 2009-04-11
Well the simplest thing to do would be ignore the swap issue and deal with that next time you are reinstalling. To add the other partition to fstab

Make a folder for it to mount in - change name to suit you - make sure to repeat change in fstab

```
sudo mkdir /media/sda1
```

Now backup and edit fstab
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add these to end of the file

```

##dev/sda1
/dev/sda1 /media/sda1 ext3 user,relatime 0 2
```

Check it mounts

```
sudo mount -a
```

---

### Post by mlnease on 2009-04-11
> **forestpixie said:**
> Well the simplest thing to do would be ignore the swap issue and deal with that next time you are reinstalling. To add the other partition to fstab

Make a folder for it to mount in - change name to suit you - make sure to repeat change in fstab

```
sudo mkdir /media/sda1
```

Now backup and edit fstab
```
sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab
```

Add these to end of the file

```

##dev/sda1
/dev/sda1 /media/sda1 ext3 user,relatime 0 2
```

Check it mounts

```
sudo mount -a
```

Very useful and helpful-- 

I didn't realize that cleaning up the Grub menu (as I thought of it) was a swap issue.  Can you recommend a resource for learning to deal with this--either now or on the occasion of my next reinstallation?

Thanks loads again for your time and patience.

mike

---

### Post by mlnease on 2009-04-11
> **Therion said:**
> Maybe it's time to reformat and do a fresh install?

It's a tempting thought, but reinstalling hasn't been so simple lately--that's how I've acquired all this clutter, just in the last few days.  I suspect a hardware problem that I can't diagnose (hard drive, maybe) because I've installed Ubuntu before many times on many different hard drives without a hitch.  This time it took me maybe six tries before I got one that worked.  So the REALLY simple solution would probably be a new computer but that, alas, is not in the budget.

So if there's a way you could recommend to remove the junk while keeping the present working installation--or if you could direct me to a resource for figuring this out online--I'd be most appreciative.  If not, thanks again just the same for your time.

mike

---

### Post by Elfy on 2009-04-11
> **mlnease said:**
> Very useful and helpful-- 

I didn't realize that cleaning up the Grub menu (as I thought of it) was a swap issue.  Can you recommend a resource for learning to deal with this--either now or on the occasion of my next reinstallation?

Thanks loads again for your time and patience.

mike

> **mlnease said:**
> It's a tempting thought, but reinstalling hasn't been so simple lately--that's how I've acquired all this clutter, just in the last few days.  I suspect a hardware problem that I can't diagnose (hard drive, maybe) because I've installed Ubuntu before many times on many different hard drives without a hitch.  This time it took me maybe six tries before I got one that worked.  So the REALLY simple solution would probably be a new computer but that, alas, is not in the budget.

So if there's a way you could recommend to remove the junk while keeping the present working installation--or if you could direct me to a resource for figuring this out online--I'd be most appreciative.  If not, thanks again just the same for your time.

mike

Not really sure what you are hoping to achieve further than dealing with the spare partition.

As far as resources go - there are the various docs 

[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[https://help.ubuntu.com/](https://help.ubuntu.com/)

There is obviously the forum - while searching with the forum search is less than satisfactory, I use uboontu.com which will also search in various categories once the first search is done.

Further you can use IRC to get help

[https://help.ubuntu.com/community/InternetRelayChat](https://help.ubuntu.com/community/InternetRelayChat)

---

