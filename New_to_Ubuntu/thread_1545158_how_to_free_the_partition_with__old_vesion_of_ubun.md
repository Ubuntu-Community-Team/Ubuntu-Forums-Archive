---
title: "how to free the partition with  old vesion of ubuntu"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by med412004 on 2010-08-03
I had on my laptop windows vista & ubuntu 2.5 yrs back. recently i installed windows 7 after which the ubuntu simply disappeared.so I reinstalled the newer vesion of ubuntu. Now on my boot up screen i get option for all the three- windows 7, old ubuntu & new ubuntu. 
I want to uninstall the old ubuntu vesion & use that harddisk space in windows or may be new ubuntu. how to do it?
please consider that i am just an average user working in non technical field; not some computer engineer.

p.s. I hardly used the old ubuntu, it was too unfriendly for a non technical person like me, but the new version looks interesting and i want to try it. it would help if such basic problems of installation dont arise or at least there is some help about installation problems in understandable language  in FAQ section.

---

### Post by cj.surrusco on 2010-08-03
When you say that the old Ubuntu "simply disappeared" do you mean that the partition was deleted? Show the output of: 
```
sudo fdisk -l
```

---

### Post by med412004 on 2010-08-04
no it was not deleted. it just became invisible after loading windows 7(my system would start directly in windows and windows did not show it in disk manager). however while loading new ubuntu it was there. ubuntu did not give option of deleting it, it showed a bar with a slider to choose size of partition.

---

### Post by tarps87 on 2010-08-04
> **cj.surrusco said:**
> When you say that the old Ubuntu "simply disappeared" do you mean that the partition was deleted? Show the output of: 
```
sudo fdisk -l
```

> **med412004 said:**
> no it was not deleted. it just became invisible after loading windows 7(my system would start directly in windows and windows did not show it in disk manager). however while loading new ubuntu it was there. ubuntu did not give option of deleting it, it showed a bar with a slider to choose size of partition.

windows just installed it's boot loader over grub removing the option to boot Ubuntu.
Deleting the partition/old install is just a case of booting the live cd, opening gparted, select the old Ubuntu partition and delete it. Now resize the new Ubuntu partition.
The grub/boot menu will then need updating to remove the option

Could you post the output of sudo fdisk -l as cj.surrusco suggested, then we can provide more detailed help

---

### Post by med412004 on 2010-08-06
what is "sudo fdisk -l"

---

### Post by indytim on 2010-08-06
1.  Go to the terminal.

2.  At the "$" prompt:

```

sudo fdisk -l <Enter Key>

```

3.  Post the result back here.

IndyTim / DataMan

---

### Post by med412004 on 2010-08-06
[FONT=monospace]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18201820

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4463    35840000    7  HPFS/NTFS
/dev/sda2            4463        8924    35840000    7  HPFS/NTFS
/dev/sda3            8924       14024    40960000    7  HPFS/NTFS
/dev/sda4           14025       19457    43640542    5  Extended
/dev/sda5           14025       15602    12673360   83  Linux
/dev/sda6           17764       19457    13607023+  82  Linux swap / Solaris
/dev/sda7           15602       17667    16586752   83  Linux
/dev/sda8           17667       17763      772096   82  Linux swap / Solaris

Partition table entries are not in disk order

[/FONT]

---

