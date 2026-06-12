---
title: "Dual Boot Ubuntu and XP. How to I format the XP partition and install Vista instead?"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by arce on 2009-04-06
Ok I have Dual boot XP and Ubuntu.

How do I install Vista over XP in the other partition?

Typically you boot up to the CD with the OS on it. How is it done when you boot up and you have the option to Go to Ubuntu or XP?

---

### Post by presence1960 on 2009-04-06
> **arce said:**
> Ok I have Dual boot XP and Ubuntu.

How do I install Vista over XP in the other partition?

Typically you boot up to the CD with the OS on it. How is it done when you boot up and you have the option to Go to Ubuntu or XP?

There are a couple of ways to do this. this is what I would do.

1. Make sure your BIOS is set to boot from CD. Boot Ubuntu Live CD and use gparted (Partition Editor) to delete the XP partition. Then create a NTFS patrtion from the resulting unallocated space. Evit the Live CD and then boot from the Vista CD. Install Vista to the NTFS partition. After installing Vista note that Vista will have overwritten GRUB. You will then have to restore GRUB. Do This:

1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Go SuperUser (that is, type "sudo -s"). Enter root passwords as 
   necessary.
4. Type "grub"
5. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
6. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
7. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
8. Quit grub by typing "quit".
9. Reboot and remove the bootable CD.

I am assuming your windows and Ubuntu partitions are on the same physical HDD.

I dual boot and I prefer XP over Vista. I have an OEM version of Vista Home Premium and IMO it is junk. But you can use it if you want to. I think XP is less of a hassle and more stable.

---

### Post by arce on 2009-04-06
Both partitions are on the same HD.

---

### Post by presence1960 on 2009-04-06
> **arce said:**
> Both partitions are on the same HD.

you should be good to go then.

---

### Post by kansasnoob on 2009-04-06
Presence1960 did a good job!

But you should first know about Ubuntu partitions!

Like here is my output of:

```
sudo fdisk -l
```

> lance@lance-desktop:~$ sudo fdisk -l
[sudo] password for lance: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63056305

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2677    21502971    7  HPFS/NTFS
/dev/sda2            2678        9729    56645190    5  Extended
/dev/sda5            2678        5035    18940603+  83  Linux
/dev/sda6            5036        5169     1076323+  82  Linux swap / Solaris
/dev/sda7            5170        5934     6144831   83  Linux
/dev/sda8            5935        7434    12048718+  83  Linux
/dev/sda9            7435        8199     6144831   83  Linux
/dev/sda10           8200        9729    12289693+  83  Linux


The (a) in sda means hard drive #1! the (1) in sda1 means partition #1, sda2 means drive #1, partition #2. sdb1 would mean Hard drive #2, partition #1!

So you'd want to use gparted (aka: Partition Editor) from your Ubuntu install (you'll have to install it from Synaptic) and locate your XP partition and delete it. Of course I'm assuming you've backed up all the info you want to save from XP!

Now I'm going to confuse you more! GRUB does numbering beginning with 0 (zero) so sda1 becomes hd(0,0), sda2 would become hd(0,1), etc.

Are you confused yet?

---

### Post by pastalavista on 2009-04-06
I don't think you'll be any happier with Vista than you were with XP... it's just prettier.. and a lot slower. Why are you "upgrading"?

---

### Post by presence1960 on 2009-04-06
> **pastalavista said:**
> I don't think you'll be any happier with Vista than you were with XP... it's just prettier.. and a lot slower. Why are you "upgrading"?

+1

IMO Vista is an exercise in futility. I think that was as nice as I can be! :guitar:

---

### Post by arce on 2009-04-07
Yeah you made it more confusing. I will try it this weekend, But I will try Home Edition of XP. The pro version I have been using is very unstable. 

I had Home Edition on the computer before the first install and it worked perfect. I decided to try Pro and it has given me nothing but trouble.

---

### Post by arce on 2009-04-07
Ok I installed Gparted

So first I have to do what you said kansasnoob?

Then I have to do what you said Presence1960 ?

---

### Post by presence1960 on 2009-04-08
> **arce said:**
> Ok I installed Gparted

So first I have to do what you said kansasnoob?

Then I have to do what you said Presence1960 ?

I believe kansasnoob wanted you to look at your partitions setup to be sure you know which partitions are which. run in terminal ```
sudo fdisk -l
``` that is a lowercase L

you'll get something like this:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa7a57e45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16840   135267268+  83  Linux
/dev/sda2           16841       18389    12442342+  83  Linux
/dev/sda3           18390       19457     8578710    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000d179

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sdb2            2612        4569    15727635   83  Linux
/dev/sdb3            4570       29879   203302575   83  Linux
/dev/sdb4           29880       30401     4192965   82  Linux swap / Solaris
```

From that I can see my XP partition is sdb1. That would be the one for me to delete. So fire up Gparted. As long as your windows partition is not mounted you can delete it from Ubuntu or use gparted from Live CD. Find your windows partition in gparted. Right click on it>choose delete. Click apply. This will leave unallocated space. Right click on unallocated space and choose New. Make it an NTFS partition and click apply. When completed you are ready to install windows to that newly created NTFS partition.

---

### Post by arce on 2009-04-08
I'm going to attempt it this weekend. I have school all week:(

I have to say I have never been a part of such a helpful forum with great people.


 Once I get Ubuntu down I'm going to remove XP also.

---

