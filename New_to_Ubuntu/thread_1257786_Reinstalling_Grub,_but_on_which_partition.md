---
title: "Reinstalling Grub, but on which partition?"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by Quakky on 2009-09-04
k making long story short.

Had XP+Ubuntu. installed Win7, lost ubuntu. waited like 4 months. reinstalled Ubuntu because new version came out and had nothing on old one that I cant access. after re-installation I still cant see the boot up option for Ubuntu.

So I followed "https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows" and that did not help me I got a weird error . Doing --recheck didnt help. 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fc70fc7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68a2f0c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      108546   871895713+   7  HPFS/NTFS
/dev/sdb2          108547      121601   104864287+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfd0505d7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       26484   212732698+   7  HPFS/NTFS
/dev/sdc2           30254       30401     1188810   82  Linux swap / Solaris
/dev/sdc3           26485       30253    30274492+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdd: 8011 MB, 8011087872 bytes
32 heads, 63 sectors/track, 7761 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x72766212

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        7761     7823056+   b  W95 FAT32



according to this info above, how should I go about feeding the terminal commands to get GRUB to start showing up? 

I did mkdir /media/root, mount /dev/sdc3 /media/root, sudo grub-install --root-directory=/media/root /dev/sdc.
I get an error saying that "device.map" cannot be opened, but then it says GRUB installed successfully. 

Please help me get Ubuntu started

Please note that Windows 7 made itself default OS, and is  dev/sdc1 * 1 26484 212732698+ 7 HPFS/NTFS

---

### Post by Zimmer on 2009-09-04
Can you boot Win7? 
If yes, then my suggestion is as follows (works for me with Vista Dual boot)
Boot Win 7
Download EasyBCD 1.7.2 - NeoSmart Technologies
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

You have installed GRUB (it would appear) to sdc3 , you can check this by using a live cd and browsing that partition and check GRUB is installed..

Back in Win7 point EasyBCD to the Ubuntu on sdc3 
see 
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

for an example.
.better still
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)  (EDIT
or
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)  (EDIT)


.. if things are not quite right it might be worth re installing Ubuntu and when asked the question 'where do you want to install GRUB?' put it on the partition you install Ubuntu to, then tweak Easy BCD to suit! as per the previous link's instructions.

Hope this helps
Zimmer

---

### Post by Penguin Guy on 2009-09-04
Boot into an Ubuntu liveCD and run the following commands:
```

grub
root(hd2,2)
setup(hd0)  *# or setup(hd2) or setup(hd2,2) (not 100% sure)*

```

---

### Post by Quakky on 2009-09-04
the thing is I am installing GRUB on the partition that ubuntu is installed on (sdc3) which is confusing the hell outta me on how GRUB is not loading.

I'm doing everything correctly but for some reason, windows 7's bootloader does not get deleted AND it always comes up.

Edit:Also, I can boot into windows 7 and windows XP just fine..no issues
Edit2: wow Why is this BCD solution not a sticky in ubuntu forums? I basically followed the directions of "http://neosmart.net/wiki/display/EBCD/Ubuntu" and 10 mins later I'm in my Ubuntu downloading updates.


@Zimmer. thx alot man..that was really helpful link lol

---

### Post by Zimmer on 2009-09-04
The reason Win7 keeps taking over is that Win has control of the MBR (Master Boot Record) . I had a link to a great website that gave you all the info on how windows booted and controlled multiboot of it's products, I may go look for it and post it here for you.
If you overwrite the MBR with the GRUB info oft times you cannot get back to your Win systems. As you have seen the simple answer is to load GRUB in the Linux partition and make use of Windows BCD to access it. 

*Zimmer slips away to look for that link...

[http://www.multibooters.co.uk/](http://www.multibooters.co.uk/)

Found!

---

