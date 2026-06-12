---
title: "GRUB reinstall driving me crazy"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by Dookert on 2009-12-12
Okay recently had to do my monthly reinstall of XP. obviously it wiped grub. I like grub, I want it back, but so far it has been impossible to reinstall. I am a noob to this.

My drives look like this.

XP is on hd0 partition 1
hd0 partion 2 is NTFS space for windows media apps etc.

hd1 partition 1 is also NTFS space for windows media

hd1 partion 2 has ubuntu 9.1 on it. 

Following EVERY single freakin list of tutorials to reinstall grub has led to utter frustration.

Ive followed this link [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to a T with no results. 

the command [FONT=monospace]: [/FONT]find /boot/grub/stage1 
ends up giving an Error 15 missing file error. 

like I said following the above link addresses this, even after mounting the drive, changing to root, whatever I STILL get the missing file error

If I try sudo grub:
Grub> root (hd0,1)
Grub> setup (hd0)

I get an error 17 could not mount the selected partition or whatever.

Im about to just reinstall ubuntu again because its driving me crazy which is rediculous. Why does this have to be so hard? why cant somebody just make an executable to freakin install it to your MBR? like FIXMBR in windows recovery. Instead its an endless stream of command lines and errors. 

somebody please tell me im doing something fundamentally wrong!

-On the brink

---

### Post by ~sHyLoCk~ on 2009-12-12
You're doing it wrong. Don't get confused. That tutorial is for Grub-legacy, where as 9.10 has grub2.

1. Boot from ubuntu live cd.
2. sudo fdisk -l

See the o/p , usually it's /dev/sdaN [where N>0 ; N is an integer]

3. sudo grub-install /dev/sda

I hope it's still called grub-install , else try to press tab after typing grub and see if there's a grub2-install. 
<--LILO user here. :p

EDIT: I just found this: [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by presence1960 on 2009-12-13
> **Dookert said:**
> Okay recently had to do my monthly reinstall of XP. obviously it wiped grub. I like grub, I want it back, but so far it has been impossible to reinstall. I am a noob to this.

My drives look like this.

XP is on hd0 partition 1
hd0 partion 2 is NTFS space for windows media apps etc.

hd1 partition 1 is also NTFS space for windows media

hd1 partion 2 has ubuntu 9.1 on it. 

Following EVERY single freakin list of tutorials to reinstall grub has led to utter frustration.

Ive followed this link [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) to a T with no results. 

the command [FONT=monospace]: [/FONT]find /boot/grub/stage1 
ends up giving an Error 15 missing file error. 

like I said following the above link addresses this, even after mounting the drive, changing to root, whatever I STILL get the missing file error

If I try sudo grub:
Grub> root (hd0,1)
Grub> setup (hd0)

I get an error 17 could not mount the selected partition or whatever.

Im about to just reinstall ubuntu again because its driving me crazy which is rediculous. Why does this have to be so hard? why cant somebody just make an executable to freakin install it to your MBR? like FIXMBR in windows recovery. Instead its an endless stream of command lines and errors. 

somebody please tell me im doing something fundamentally wrong!

-On the brink

Boot from 9.10 Live CD, choose "try ubuntu without any changes", when desktop loads open a terminal and run ```
sudo mount /dev/sdb2 /mnt
```

Then run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot without Live CD. Go into BIOS and set sdb as first hard disk to boot. Save changes to CMOS and continue booting. Boot into Ubuntu, open a terminal and run ```
sudo update-grub
```

I would advise to run ```
sudo fdisk -l
``` before running those commands to verify Ubuntu is installed on the sdb disk in sdb2. If it isn't adjust the commands to match .

Here is the link to follow FYI: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Dookert on 2009-12-13
just to be cautious . Here's a loot at my drives.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed56ed56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925       19451    84558127+   f  W95 Ext'd (LBA)
/dev/sda5            8925       19451    84558096    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedacedac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       19457    74364885    5  Extended
/dev/sdb5           10200       18709    68356543+  83  Linux
/dev/sdb6           18710       19457     6008278+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


 Whats actually happening here? does grub write the boot loader to whatever drive you specify in: 

**sudo grub-install --root-directory=/mnt/ /dev/sdb**

wouldnt I want /dev/sdb5 ?

---

### Post by presence1960 on 2009-12-13
> **Dookert said:**
> just to be cautious . Here's a loot at my drives.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xed56ed56

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8924    71681998+   7  HPFS/NTFS
/dev/sda2            8925       19451    84558127+   f  W95 Ext'd (LBA)
/dev/sda5            8925       19451    84558096    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedacedac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       10199    81923436    7  HPFS/NTFS
/dev/sdb2           10200       19457    74364885    5  Extended
/dev/sdb5           10200       18709    68356543+  83  Linux
/dev/sdb6           18710       19457     6008278+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


 Whats actually happening here? does grub write the boot loader to whatever drive you specify in: 

**sudo grub-install --root-directory=/mnt/ /dev/sdb**

wouldnt I want /dev/sdb5 ?

you said originally 9.10 was on hd 1 partition 2. Glad you ran fdisk! it is on sdb5 (which is hd1 5th partition).

you want sdb5 in the first command. in the second command you want sdb because in order for GRUB to take over it needs to be on your MBR (sdb not sdb5). sdb5 would put GRUB on boot sector of Ubuntu partition which is useful if chainloading from another GRUB on MBR.

so first run: ```
sudo mount /dev/sdb5 /mnt
``` which will mount 9.10 root partition then run: ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
``` which will install GRUB to MBR. Then reboot & go into BIOS and set as sdb as first hard disk in hard disk boot order. Save changes to CMOS and continue booting.

---

### Post by Dookert on 2009-12-13
yeah i think a lot of the spacing is off on the sdb drive cause its got a hunk of un formatted space on it. Only thing is though my MBR is on sda1 right? it has the boot asterisk, so dont I have to do something to that too?

Also got another problem: It looks like that link posted by shylock says you have to mount the /boot partition as well? Is the "/boot" referring to sda1 with XP on it?

---

### Post by presence1960 on 2009-12-13
> **Dookert said:**
> yeah i think a lot of the spacing is off on the sdb drive cause its got a hunk of un formatted space on it. Only thing is though my MBR is on sda1 right? it has the boot asterisk, so dont I have to do something to that too?

That has the boot asterisk because windows needs a boot flag to boot whereas linux does not. You can place GRUB2 on MBR of sda. I prefer to keep GRUB on MBR of the disk linux is installed to. Every hard disk has an MBR, and BIOS controls which MBRs are looked to first when booting by the hard disk boot order in BIOS.

So in the last command you can use sda. If you use sdb then switch sdb disk to boot first in the hard disk boot order after installing GRUB.

---

### Post by Dookert on 2009-12-13
still at it. thought it was all good to go, restarted thing booted into windows. Its an older dell and the BIOS are pretty limited; it just goes right to SATA0.  you can turn  the SATA  drives on and off but thats about it from what I can tell. I suppose I could just mount the whole hard drive and then do 

[B]grub-install /dev/sda 
[/B]
right?

also. shut down SATA0 just to make sure it would boot into GRUB. It did, but I got an Error 17:failed to mount the partition. back to the drawing board

---

### Post by presence1960 on 2009-12-13
> **Dookert said:**
> still at it. thought it was all good to go, restarted thing booted into windows. Its an older dell and the BIOS are pretty limited; it just goes right to SATA0.  you can turn  the SATA  drives on and off but thats about it from what I can tell. I suppose I could just mount the whole hard drive and then do 

[B]grub-install /dev/sda 
[/B]
right?

also. shut down SATA0 just to make sure it would boot into GRUB. It did, but I got an Error 17:failed to mount the partition. back to the drawing board

Then open your machine and switch the SATA connectors on the motherboard ports so the other one becomes hd0

---

### Post by ZliaBasist on 2009-12-13
i have a lots of problems reinstaling Grub too. But this posts give me all that need to make it.

---

### Post by kansasnoob on 2009-12-13
> **Dookert said:**
> still at it. thought it was all good to go, restarted thing booted into windows. Its an older dell and the BIOS are pretty limited; it just goes right to SATA0.  you can turn  the SATA  drives on and off but thats about it from what I can tell. I suppose I could just mount the whole hard drive and then do 

[B]grub-install /dev/sda 
[/B]
right?

also. shut down SATA0 just to make sure it would boot into GRUB. It did, but I got an Error 17:failed to mount the partition. back to the drawing board

Your situation is just complex enough I'd want to see the full output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

And also the output of:

```
sudo parted /dev/sda print
```

and:

```
sudo parted /dev/sdb print
```

BTW, if this was working OK before reinstalling Windows switching sata cables might actually do more harm than good.

---

### Post by Dookert on 2009-12-13
partition table just seems like its too screwed up. I cant mount any partitions. I tried editing on startup with 'e' . changed (hd0,0) to every conceivable combination. getting either error 17's or error 25: error reading disk. I said "ef it!" simplified partition tables, reinstalled 9.10 on dev/sdb1 . everything works fine. I really hope I dont have to do this every time I have to reinstall XP

---

