---
title: "Linux mount basics -- mount multiple drives to one point"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by Jeroen Vernooij on 2009-02-17
Hi,

I have ubuntu 8.10 x86-64 on a single hard disk installed.

I also have 4 other hard disks, all with 1 NTFS partition on it containing media files. I now want all those hard disks mounted to ~/Media. 

Is it possible to add this to /etc/fstab, so all 4 disks get mounted into a single folder? 

If so, what will happen if 2 of the disks contain a file with exact the same filename but different size? Is one getting overwritten? How is this handled by linux?

I don't want to use lvm / jbod and I cannot use symlinks because of NTFS.
Also I don't want a structure like ~/Media/disk1, ~/Media/disk2 etc., for browsing simplicity.

---

### Post by JohnLM_the_Ghost on 2009-02-17
Sorry it is not possible... A single mount per mount point only (and vice versa). (btw NTFS support symlinks while in Linux enviroment)

Consider doing RAID array... that would do the thing you want...

---

### Post by Jeroen Vernooij on 2009-02-17
Ok thanks.

See, those 4 disks contain many folders with media files. If I symlink like this:
```
ln -s /dev/sdb /home/jeroen/Media
```
then I just get a symlink of sdb into ~/Media, and no symlinks of all those folders. 

Is there a way that all the folders in sdb get symlinked into ~/Media? I cannot do all of them seperately; too time-consuming. Is there a trick of some kind of trick (script?) available which makes this easier?

---

### Post by Metallion on 2009-02-17
I think that way you just linked to the device node. You should try to link the mount point instead like this:
```
ln -s /media/sdb1 /home/jeroen/Media
```

I'm not sure if it's possible to symlink multiple drives to one folder but I would guess it isn't.

---

### Post by Jeroen Vernooij on 2009-02-17
> **Metallion said:**
> 
```
ln -s /media/sdb1 /home/jeroen/Media
```


I just tried that with my USB memory stick but it also just makes a link to the disk into ~/Media (so it doesn't make links of the contents of the USB stick to ~/Media, which is what I want)

---

### Post by Jeroen Vernooij on 2009-02-17
I found a solution!!

I used this command 
```
sudo mount --bind /media/disk-1/ /home/jeroen/Media

```

Now I hope this can work for 4 disks to one point, but I can only test this later.

---

### Post by Metallion on 2009-02-17
Alright! Let us know how this goes because I'm interested.

---

### Post by Jeroen Vernooij on 2009-02-17
Sorry this will take a while (I guess 2 weeks before I can test it) but I will post it here for further reference (and I'll PM you to remember)

---

### Post by vanadium on 2009-02-17
> sudo mount --bind /media/disk-1/ /home/jeroen/Media

Don't do that. Use the symlink approach instead.
You certainly cannot mount several volumes on one location: that makes no sense. If you want several volumes to act as one storage volume, your only option is raid, as JohnLM_the_Ghost already pointed out.

Symlinks give you great flexibility. You can symlink subdirectories on disk-1, disk-2, etc in one single directory, such that all items appear together in one folder. 
```

cd /home/jeroen/Media
ln -s /media/disk-1/*
ln -s /media/disk-2/*
ln -s /media/disk-3/*

```
Using symlinks, you can organize all your data within your home folder: no need to browse outside of your home or know about mount points as a user.

---

### Post by itendo on 2009-02-17
consider me subscribed, this would be a great way of skirting buying another big new HDD right away just to consolidate the three i have orphaned from my last box

---

### Post by Metallion on 2009-02-17
> **vanadium said:**
> Don't do that. Use the symlink approach instead.
You certainly cannot mount several volumes on one location: that makes no sense. If you want several volumes to act as one storage volume, your only option is raid, as JohnLM_the_Ghost already pointed out.

Symlinks give you great flexibility. You can symlink subdirectories on disk-1, disk-2, etc in one single directory, such that all items appear together in one folder. 
```

cd /home/jeroen/Media
ln -s /media/disk-1/*
ln -s /media/disk-2/*
ln -s /media/disk-3/*

```
Using symlinks, you can organize all your data within your home folder: no need to browse outside of your home or know about mount points as a user.

Indeed that way it would work! I just kept thinking of pointing all the drives at one folder but indeed linking all the files in each drive's root would do the trick exactly!

One thing I personally don't like is how it loses the overview of what is on which drive but that's just me.

---

### Post by Jeroen Vernooij on 2009-02-17
Thank you vanadium, that is definitely a better solution. 

However, it's only creating symlinks at that point in time, so if I add another folder to one of the disks, it doesn't show up automatically into ~/Media. So I would have to put those commands in a cronjob. 

Now I'm gonna find out how to hide the symlink emblem in Nautilus because otherwise every folder has an arrow-emblem which I don't like very much.

---

### Post by JohnLM_the_Ghost on 2009-02-17
You could of course make a script to run...

btw a little tip with the linking command
(assuming your hard drives are sda, sdb, sdc, sdd all using partition one)

```
ln -s --target-directory=~/Media /media/sd{a,b,c,d}1/*
```

try changing how do you need it...

There is one caveat though... new files you save in ~/Media will end up on drive where ~/Media is on, of course... always save into those symlinked folders

---

### Post by FunkMan on 2009-05-21
How about...

Mounting to /media/Music/disk1 ; /media/Music/disk2 ; /media/Music/disk3 ; /media/Music/disk4

So you'll have all your music into /media/Music

This is the part where I'm not sure if works this way:
Then you can mount /media/Music to ~/Music.
Or you can simply mount the disks into ~/Music/disk1 ...etc.

Correct me if I'm wrong. I'm new to linux and my english isn't very good.

):P

---

### Post by JohnLM_the_Ghost on 2009-05-21
> **FunkMan said:**
> How about...

Mounting to /media/Music/disk1 ; /media/Music/disk2 ; /media/Music/disk3 ; /media/Music/disk4

So you'll have all your music into /media/Music

This is the part where I'm not sure if works this way:
Then you can mount /media/Music to ~/Music.
Or you can simply mount the disks into ~/Music/disk1 ...etc.

Correct me if I'm wrong. I'm new to linux and my english isn't very good.

):P

Well... that's roughly the same what we told...
Except you cannot mount a folder to anywhere, but you can symlink it.

---

### Post by Baelus on 2009-10-14
_

---

