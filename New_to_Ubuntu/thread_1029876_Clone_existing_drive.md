---
title: "Clone existing drive?"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by H.Callahan on 2009-01-03
How the hell do I clone an existing drive?

I have a 20Gb disk in an old machine that I want to clone and put in a newer, bigger drive.  I have tried Ghost, but every time I replace the drive, I get a problem with GRUB.  I correct that by using the Live CD and going into grub and doing:```
>root (hd0,1)
>setup (hd0)
```(there is a small Windows partition before the Ubuntu ones)

Then when I boot up, I get past Grub, but I get dumped into maintenance mode with a message that says I need to run fsck.  I run fsck and get a ton of block errors (whatever the hell they are).  I am asked after each one if I want to move it.  I reply "yes", but then another one pops up.  I usually give up after about 3000 or so of them.

Any suggestions?

---

### Post by DGortze380 on 2009-01-03
man dd

dd is capable of doing a bit for bit copy of the whole drive, should resolve some of your issues.

---

### Post by cariboo on 2009-01-03
You can use dd with the notrunc option, this will allow you to clone a smaller hdd to a larger one.

I would use the LiveCD on a computer that both has   both drives installed, then once you are at the desktop, open am Applications-->Accessories-->Terminal and type:

```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerrorsudo 
```

where /dev/sda = your 20Gb drive /dev/sdb = your new drive. To find what the device lables of the drives are before running the above command in a terminal type:

```
sudo fdisk -l
```

Jim

---

### Post by -kg- on 2009-01-04
You know, for ease of use (in a GUI environment) I really like the [Clonezilla Live CD.]("http://clonezilla.org/")  It automates a whole lot of back-up and cloning operations.  I've used it several times and it works like a champ!

Just thought I'd throw that in here for your consideration

---

### Post by H.Callahan on 2009-01-05
> **cariboo907 said:**
> ```
dd if=/dev/sda of=/dev/sdb bs=4096 conv=notrunc,noerrorsudo 
```

I tried this (I assume that the "noerrorsudo" was supposed to read just "noerror" and I was to sudo the dd command ... nothing in the --help or the man pages mentioned "noerrorsudo") and it behaved the same way as the Ghost Clone.

I will try downloading Clonezilla and see if that works any better.

Any other suggestions would be welcomed.

---

### Post by H.Callahan on 2009-01-06
Ok, Clonezilla is the same.

Any other ideas?

If I were to recreate the partitions (blank) on the new drive, is it possible with Linux to merely copy all the files (as root) from each partition to the new partition(s) and have it work normally?  I know that is not possible with Windows, but I don't know about Linux.

---

### Post by Locke_99GS on 2009-01-06
Copy the partition any way you'd like. (I just use gparted for this)

Then you need to fix grub. (I'm not at home, so i'll be going from memory here.)

```

mkdir /mnt/something
mount /dev/sda1 /mnt/something
mount -o bind /dev /mnt/something/dev
mount -t proc /mnt/something/proc
cd /mnt/someting
chroot /mnt/something
grub

```

Check the man to make sure that *mount -t proc* is correct. 

Then, within grub, finish setting up grub as you tried previously.

```

root hd0,1
setup hd0

```

Then you should be able to boot to grub on your new disk, assuming you replaced *sda1* and the *hdX,X* locations from what I mentioned.

---

### Post by dduehning on 2009-01-06
I've also used clonezilla, and found that the partitions on the new disk needed to be setup exactly as they were on the old disk (same size, etc) otherwise I would get the same boot problem you are experiencing.  I, too, have used ghost in the past, and liked the feature of resizing the image to use a single partition (in the windows world), but haven't gotten ghost to work and the only way I could get clonezilla to work was to do as I said above, and create the partitions exactly as they were before.  I did also then have to reinstall grub, but perhaps that was a noob error on my part.

I believe you should be able to move/resize after the fact using gparted.

---

