---
title: "Gparted says my wife's pendrive has a partion of -510 B?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by brawd on 2009-07-01
My wife's pendrive has been nothing but trouble. Having learned a couple of days ago about gparted I backed up and used gparted to take a look at it.

It had two partitions, both flagged as boot.
I deleted both partitions.
One showed a size of zero, the other showed a size of -512 B and therefor it won't let me carry out any more operations on it!

That's a new one on me.

Any suggestions as to creating a new single partition, then I can format with Fat32.

regards,

brawd.

---

### Post by ronaldprettyman on 2009-07-01
> **brawd said:**
> One showed a size of zero, the other showed a size of -512 B and .

Sounds corrupted
```
man mkfs.vfat
man parted
```
[color=red][size=30] don't run these commands till your sure what they do[/size][/color]
if you know the location of the drive maybe something like
/dev/sdb1 or /dev/sdc1
```
parted /dev/sdb
```
rewrite the partions
```
mkfs.vfat /dev/sdb1
```
[color=red][size=10] The above commands will destroy all data on the selected drive[/size][/color]
make it a dos filesystems

You can see your partions that are mounted with this command
```
df -h
```
you can see all partions and all drives though
gparted graphically
gparted should work but if it doesn't the above is the manual way of doing it, read the manuals and or search the commands on google

---

### Post by shad0w_walker on 2009-07-01
You can wipe out the partition table with dd (Be sure you type the commands right and get the right drive, potential data loss if you don't)

Goto the terminal (Applications > Accessories > Terminal) and run this command.

```
sudo dd if=/dev/zero of=/dev/XXX bs=512 count=1
```

Replace XXX with the drive name of the pendrive. It should show it in Gparted when you select the drive, if you're not sure, don't do anything yet and run

```
sudo fdisk -l
```

This should show a list of all the drives in your system and their partition tables. Find the one that shows the same size as you pendrive, that's your drive name.

After you've run this you should be able to open gparted and see a completely partition free pendrive listed. If it still shows the same, try unplugging the drive then plugging it back in.

Good luck.

---

### Post by brawd on 2009-07-01
This pendrive shows up as sdb and sdc

sdb is -512 B and sdc is 0. Both drives show as unallocated.

I'm grateful for your suggestions with this problem and your advice guides me in learning about the best operating system I've ever used. But, I think rather than using up your time which might be much better used on more tragic problems then far better for me to put it aside because it is of such little cost to get a replacement.

Don't worry too much about me trashing my computer - I've been doing that (albeit unintentionally) for the last 20 years and we're both still here.

Many thanks to yourselves and other helpers on the forums.

brawd.

---

### Post by oldos2er on 2009-07-01
"sdb" and "sdc" would indicate two separate drives.

---

### Post by ronaldprettyman on 2009-07-01
> **brawd said:**
> 
Don't worry too much about me trashing my computer - I've been doing that (albeit unintentionally) for the last 20 years and we're both still here.
Word
fdisk might be your best bet, had a similar problem with a scsi drive and had to rewrite the partition table after it got corrupted. I don't know the exact options but its pretty self explainitory and you can always type help in fdisk or
info fdisk
man fdisk

good luck

---

