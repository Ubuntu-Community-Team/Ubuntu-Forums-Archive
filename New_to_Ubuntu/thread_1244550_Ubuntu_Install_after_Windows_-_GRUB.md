---
title: "Ubuntu Install after Windows - GRUB"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by slrohn on 2009-08-19
I've searched the forums and Google, I admit to a lack of thoroughness in this endeavor, but frustration is getting the better of me.

[queue unrelated rant about Vista refusing to play nice with front audio jacks]

Long story short, I've finally gotten around to fixing my desktop install of Ubuntu 9.04 (64-bit) and I'm running into confusion more than actual problems. I don't want to mess up the boot loader ( as I have before :D ) and have to add that to my pile of computer fix-its.

I have 9.04 installed with manually created / , /home , swap partitions. I only want to format and reinstall the root partition.

```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
[COLOR="SeaGreen"]/dev/sda1   *           1       94488   245760000    7  HPFS/NTFS
/dev/sda2           94489      187768   242621280    5  Extended[/COLOR]
[COLOR="Red"]/dev/sda5           94489      109505    39059191+  83  Linux[/COLOR]
[COLOR="RoyalBlue"]/dev/sda6          109506      178964   180662833+  83  Linux[/COLOR]
/dev/sda7          178965      187768    22899178+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d67d5bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30157   242236071   83  Linux
/dev/sdb2           30158       60801   246147930   83  Linux

```

/dev/sda is the only hard drive I'm concerned with. /dev/sdb is just for backup data and random storage; nothing is bootable.

[COLOR="SeaGreen"]/dev/sda1[/COLOR] and [COLOR="SeaGreen"]/dev/sda2[/COLOR] are Windows-y bits.
[COLOR="Red"]/dev/sda5[/COLOR] is my root partition.
[COLOR="RoyalBlue"]/dev/sda6[/COLOR] is my /home partition.

My main question, where do I install GRUB? Going through the installer w/the Live CD, I set the old / partition to be formated, with no changes to anything else. In the Advanced... button dialog, which device do I set for the boot loader installation? (without screwing up my MBR, etc.)

```

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #7 of SCSI1 (0,0,0) (sda) as swap

```

As I'm writing this post, I've found a new thing to confuse me. Look at the starting points for /sda2 and /sda5 .
```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
[COLOR="SeaGreen"]/dev/sda1   *           1       94488   245760000    7  HPFS/NTFS
/dev/sda2           94489      187768   242621280    5  Extended[/COLOR]
[COLOR="Red"]/dev/sda5           94489      109505    39059191+  83  Linux[/COLOR]

```

Why are they the same? :( Is this a bigger problem that I need to address, or is there some logical reason why my root partition starts at the same cylinder as my Windows drive?

It's been a while since I installed 9.04 on this machine, so I don't remember what I did or why the devices would be sitting on top of each other.

Oh, today is not my day for computer stuff.

Helps.

---

### Post by LewRockwell on 2009-08-19
> **slrohn said:**
> I've searched the forums and Google, I admit to a lack of thoroughness in this endeavor, but frustration is getting the better of me.

[queue unrelated rant about Vista refusing to play nice with front audio jacks]

Long story short, I've finally gotten around to fixing my desktop install of Ubuntu 9.04 (64-bit) and I'm running into confusion more than actual problems. I don't want to mess up the boot loader ( as I have before :D ) and have to add that to my pile of computer fix-its.

I have 9.04 installed with manually created / , /home , swap partitions. I only want to format and reinstall the root partition.

```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
[COLOR="SeaGreen"]/dev/sda1   *           1       94488   245760000    7  HPFS/NTFS
/dev/sda2           94489      187768   242621280    5  Extended[/COLOR]
[COLOR="Red"]/dev/sda5           94489      109505    39059191+  83  Linux[/COLOR]
[COLOR="RoyalBlue"]/dev/sda6          109506      178964   180662833+  83  Linux[/COLOR]
/dev/sda7          178965      187768    22899178+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d67d5bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30157   242236071   83  Linux
/dev/sdb2           30158       60801   246147930   83  Linux

```

/dev/sda is the only hard drive I'm concerned with. /dev/sdb is just for backup data and random storage; nothing is bootable.

[COLOR="SeaGreen"]/dev/sda1[/COLOR] and [COLOR="SeaGreen"]/dev/sda2[/COLOR] are Windows-y bits.
[COLOR="Red"]/dev/sda5[/COLOR] is my root partition.
[COLOR="RoyalBlue"]/dev/sda6[/COLOR] is my /home partition.

My main question, where do I install GRUB? Going through the installer w/the Live CD, I set the old / partition to be formated, with no changes to anything else. In the Advanced... button dialog, which device do I set for the boot loader installation? (without screwing up my MBR, etc.)

```

The following partitions are going to be formatted:
 partition #5 of SCSI1 (0,0,0) (sda) as ext3
 partition #7 of SCSI1 (0,0,0) (sda) as swap

```

As I'm writing this post, I've found a new thing to confuse me. Look at the starting points for /sda2 and /sda5 .
```


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
102 heads, 51 sectors/track, 187768 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
[COLOR="SeaGreen"]/dev/sda1   *           1       94488   245760000    7  HPFS/NTFS
/dev/sda2           94489      187768   242621280    5  Extended[/COLOR]
[COLOR="Red"]/dev/sda5           94489      109505    39059191+  83  Linux[/COLOR]

```

Why are they the same? :( Is this a bigger problem that I need to address, or is there some logical reason why my root partition starts at the same cylinder as my Windows drive?

It's been a while since I installed 9.04 on this machine, so I don't remember what I did or why the devices would be sitting on top of each other.

Oh, today is not my day for computer stuff.

Helps.

your sda2 is assigned as your extended partition(so it is not part of your "windows bits" as you previously described)

your sda5 is the first logical partition inside your extended partition so these will have the same starting point

in an earlier portion of your post(first code box) you can see this shown

.

---

### Post by michy99 on 2009-08-19
/dev/sda2 is an extended partition which contains the logical partitions /dev/sda5 /dev/sda6 and /dev/sda7.

Edit: LewRockwell beat me to it.

---

### Post by slrohn on 2009-08-19
> your sda2 is assigned as your extended partition
your sda5 is the first logical partition inside your extended partition so these will have the same starting point

Ok, my sense of dread has dissipated. Thanks.

Anyone have advice re: GRUB and which device to install it to?

---

### Post by LewRockwell on 2009-08-19
> **slrohn said:**
> Ok, my sense of dread has dissipated. Thanks.

Anyone have advice re: GRUB and which device to install it to?

Grub will place itself in your MBR and direct itself to your /boot/grub/menu.lst file(which is most often/normally in your "/" partition)

.

---

### Post by raymondh on 2009-08-19
To confirm what Lew was saying, here's a cut/copy of my fdisk -l

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      204800    7  HPFS/NTFS
/dev/sda2              26       10888    87246266    7  HPFS/NTFS
/dev/sda3           10888       91201   645117480    5  Extended
/dev/sda5           10888       20614    78125008+  83  Linux
/dev/sda6           20614       90460   561035128+  83  Linux
/dev/sda7           90460       91201     5957248+  82  Linux swap / Solaris

---

### Post by slrohn on 2009-08-19
> **LewRockwell said:**
> Grub will place itself in your MBR and direct itself to your /boot/grub/menu.lst file(which is most often/normally in your "/" partition)

.

So, I should keep it with the default device, (hd0) ?

---

### Post by LewRockwell on 2009-08-19
> **slrohn said:**
> So, I should keep it with the default device, (hd0) ?

yes, if you have previously installed grub AND you are re-using the same partition for your "/" then the portion of your grub that is located in the MBR will remain the same

.

---

### Post by LewRockwell on 2009-08-19
here are some links to grub info:

[http://ubuntuforums.org/showpost.php?p=7812667&postcount=2](http://ubuntuforums.org/showpost.php?p=7812667&postcount=2)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)


also, we would like to note that learning to edit the grub menu file is fun, rewarding, and educational

you'll learn not only how to effectively administer the grub menu but you might also have some fun adding famous quotations and notes to yourself and/or others/loved-ones

.

---

### Post by LewRockwell on 2009-08-19
and we might as well add:

you'll want to make a back-up/copy of your grub menu file BEFORE you start kicking it around...so into the terminal we gooooooo.....```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```and you can check that by```
cd /boot/grub "enter"
ls "enter"
```and you should see both the original and the backup

then, to start a READ AND WRITE editing session you will```
gksudo gedit /boot/grub/menu.lst
```

.

---

### Post by slrohn on 2009-08-19
Awesome, everything is safe and sound. Thanks a bunch :)

---

